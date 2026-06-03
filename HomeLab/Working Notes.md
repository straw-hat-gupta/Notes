
aaea4b0f-fad7-4592-9fe6-b0beaa42ff7b


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104 [GeForce GTX 1070] [10de:1b81] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GP104 High Definition Audio Controller [10de:10f0] (rev a1)


options vfio-pci ids=10de:1b81,10de:10f0 disable_vga=1


Here is a clean summary you can paste into another chat.


---

# Ollama Testing Results

I installed Ollama first and tested models.

Installed models included:

```text
qwen3.5:9b-q4_K_M
gemma3:4b
llama3.1:8b
```

Important test result:

```bash
ollama ps
```

For Qwen:

```text
qwen3.5:9b-q4_K_M
SIZE: 12 GB
PROCESSOR: 88%/12% CPU/GPU
CONTEXT: 4096
```

Meaning:

```text
The model was mostly offloaded to CPU/RAM.
Only about 12% was on GPU.
VRAM usage was only around 1.4 GB.
```

Why:

```text
The Qwen 9B Q4 model file is 6.6 GB, but runtime memory was about 12 GB.
The GTX 1070 has only 8 GB VRAM.
So Ollama could not fit the full model on GPU.
```

For Llama:

```text
llama3.1:8b used about 5.3 GB VRAM
```

This worked much better and fit the GPU more cleanly.

Important concept:

```text
Model file size is not the same as runtime memory.
Runtime memory includes model weights, KV cache, compute buffers, context, and overhead.
```

Also:

```text
nvidia-smi GPU-Util showing 0% can be normal if the model is idle.
VRAM usage shows the model is loaded.
GPU utilization only spikes while actively generating.
```

Useful commands:

```bash
ollama list
ollama ps
ollama run model-name --verbose
watch -n 1 nvidia-smi
nvidia-smi dmon -s pucm -d 1
```

---

# Ollama Modelfile Notes

I created a Modelfile to reduce context size.

Example:

```text
FROM qwen3.5:4b
PARAMETER num_ctx 2048
```

This is syntactically correct.

To reduce context for the 9B Qwen model, it should be:

```text
FROM qwen3.5:9b-q4_K_M
PARAMETER num_ctx 2048
```

Then create it with:

```bash
ollama create qwen35-9b-ctx2k -f Modelfile.qwen-lowctx
```

Check with:

```bash
ollama ps
```

Expected context should show:

```text
2048
```

However, reducing context may not fully fix Qwen 9B because the runtime memory is still too large for 8 GB VRAM.

---

# Decision: Move from Ollama to llama.cpp

I decided to stop using Ollama and switch to `llama.cpp` because I want more control over model execution.

Reason:

```text
Ollama is convenient but hides low-level performance knobs.
llama.cpp lets me control GPU layers, context size, CPU threads, batch size, server mode, and benchmarking.
```

Planned llama.cpp setup:

```text
llm-gpu VM
├── Ubuntu 24.04
├── NVIDIA driver working
├── CUDA support
├── llama.cpp built with CUDA
├── GGUF models stored in /srv/models
└── llama-server exposed over LAN
```

Recommended model directory:

```text
/srv/models/
├── qwen/
├── llama/
├── gemma/
└── test/
```

Basic setup plan:

```bash
sudo mkdir -p /srv/models
sudo chown -R $USER:$USER /srv/models

sudo apt update
sudo apt install -y git build-essential cmake ninja-build curl libcurl4-openssl-dev python3 python3-pip python3-venv
```

Build llama.cpp:

```bash
cd /opt
sudo git clone https://github.com/ggml-org/llama.cpp.git
sudo chown -R $USER:$USER /opt/llama.cpp
cd /opt/llama.cpp

cmake -B build -DGGML_CUDA=ON -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release -j$(nproc)
```

Test binaries:

```bash
./build/bin/llama-cli --help
./build/bin/llama-server --help
./build/bin/llama-bench --help
```

Example llama.cpp run:

```bash
./build/bin/llama-cli \
  -m /srv/models/llama/llama-3.1-8b-q4_k_m.gguf \
  -p "Explain what a Proxmox cluster is in simple terms." \
  -n 256 \
  -c 2048 \
  -ngl 99 \
  -t 6
```

Important llama.cpp options:

```text
-m
Path to GGUF model

-p
Prompt

-n
Number of tokens to generate

-c / --ctx-size
Context size

-ngl / --n-gpu-layers
How many layers to offload to GPU

-t / --threads
CPU threads
```

For the GTX 1070 8 GB:

```text
4B models: ctx 4096, n-gpu-layers 99
8B models: ctx 2048, n-gpu-layers 99
9B models: ctx 1024 or 2048, n-gpu-layers 99 first, reduce if needed
```

---

# llama.cpp Server Plan

The local model should eventually run as a server in the `llm-gpu` VM.

Example:

```bash
./build/bin/llama-server \
  --host 0.0.0.0 \
  --port 8080 \
  --model /srv/models/llama/llama-3.1-8b-q4_k_m.gguf \
  --ctx-size 2048 \
  --n-gpu-layers 99 \
  --threads 6 \
  --parallel 1
```

Then test locally:

```bash
curl http://localhost:8080/health
```

And from another machine:

```bash
curl http://10.44.0.xxx:8080/health
```

The agent harness VM can later call this local LLM server over HTTP.

---

# VM vs LXC for llama.cpp

I asked whether llama.cpp should run in an LXC instead of a VM.

Current recommendation:

```text
Keep llama.cpp in the Ubuntu VM with GPU passthrough.
```

Why:

```text
GPU passthrough is already working
NVIDIA driver is already working inside the VM
Better isolation
Cleaner CUDA setup
Less risk of breaking the Proxmox host
Near-native GPU performance
```

LXC would be lighter, but more annoying because it usually requires:

```text
NVIDIA driver on Proxmox host
Passing /dev/nvidia* into the container
Matching CUDA libraries
More permission/container complexity
```

Conclusion:

```text
Use VM for main CUDA LLM server.
Use LXCs for supporting services like monitoring, RAG, Grafana, Prometheus, APIs, small tools.
```

---
---

# Current Immediate Next Step

I removed or stopped Ollama and want to fully switch to llama.cpp.

Need to verify how Ollama was installed because:

```bash
sudo apt remove ollama
```

failed with:

```text
No apt package "ollama"
```

But:

```bash
ollama -h
```

still works.

Likely installed via official script or Snap.

Commands to diagnose:

```bash
which ollama
type -a ollama
snap list | grep -i ollama
dpkg -l | grep -i ollama
systemctl status ollama --no-pager
```

If installed by script, remove with:

```bash
sudo systemctl stop ollama 2>/dev/null
sudo systemctl disable ollama 2>/dev/null
sudo rm -f /etc/systemd/system/ollama.service
sudo systemctl daemon-reload
sudo rm -f /usr/local/bin/ollama
```

Optionally remove models later:

```bash
sudo rm -rf /usr/share/ollama
```

Final check:

```bash
which ollama
systemctl status ollama --no-pager
nvidia-smi
ss -tulpn | grep 11434
```

Good state:

```text
ollama command not found
ollama service inactive or missing
no ollama process in nvidia-smi
nothing listening on port 11434
```

---

# Key Lessons Learned

```text
1. Proxmox users and Linux users inside guests are separate.

2. VM MAC addresses are different from the physical host MAC because VMs use virtual NICs.

3. A disk showing under Proxmox Disks is not automatically usable for VMs until added as storage.

4. LVM-thin is a good local VM disk storage option.

5. Node Exporter metrics on port 9100 working means the node is scrapeable by Prometheus.

6. PVE exporter on port 9221 showing a simple page is normal.

7. Model file size is not runtime VRAM usage.

8. 8 GB VRAM is the main constraint for local LLMs.

9. Ollama hides too much optimization detail.

10. llama.cpp is better for tuning GPU layers, context size, CPU threads, and benchmarks.

11. For the GPU model server, a VM with passthrough is cleaner than LXC.

12. For monitoring and supporting services, LXC is usually better than a VM.
```