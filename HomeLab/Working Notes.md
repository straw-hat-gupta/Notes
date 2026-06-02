
aaea4b0f-fad7-4592-9fe6-b0beaa42ff7b


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104 [GeForce GTX 1070] [10de:1b81] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GP104 High Definition Audio Controller [10de:10f0] (rev a1)


options vfio-pci ids=10de:1b81,10de:10f0 disable_vga=1


Here is a clean summary you can paste into another chat.

---

# Homelab Setup Summary

I am building a Proxmox-based homelab cluster to run local LLMs, monitoring, storage, and later an AI agent harness. The goal is to use the cluster for local model serving, RAG, monitoring, and automation while maximizing use of older hardware.

## Current Proxmox Cluster

Cluster name:

```text
homelab
```

Network:

```text
10.44.0.0/24
```

Main nodes:

```text
pve-d1
IP: 10.44.0.50
CPU: i7-4790
RAM: 32 GB
GPU: NVIDIA GTX 1070 / 1070 Ti class GPU, 8 GB VRAM
Boot disk: 128 GB SATA SSD
Extra disk: 256 GB Samsung SSD configured as LVM-thin storage
Role: Main GPU/LLM node

pve-d2
IP: 10.44.0.51
CPU: i7-4790
RAM: 16 GB
Boot disk: 256 GB SATA SSD
Role: General compute node

pve-6420
IP: 10.44.0.52
CPU: i5-2520M
RAM: 6 GB
Disk: 320 GB HDD
Role: Lightweight cluster node

pve-7450
IP: 10.44.0.53
CPU: i7-5600U
RAM: 16 GB
Boot disk: 128 GB SATA SSD
Role: General lightweight node

pve-storage
IP: 10.44.0.54
CPU: i5-3570
RAM: 24 GB
Boot disk: 128 GB SATA SSD
Extra storage: 2x 1 TB HDD, 1x 128 GB SSD
Role: Storage node
```

The cluster is working and all nodes have been joined successfully. Enterprise repositories were disabled and Proxmox no-subscription repos were enabled.

---

# Network Setup

I changed the home network from `10.0.0.x` to `10.44.0.x` to avoid conflicts with another network that may also use `10.0.0.x`, especially because both networks use Tailscale.

Proxmox host IPs are static/reserved in the router.

Important idea learned:

A VM gets its own virtual NIC and its own MAC address. That is why the VM MAC address is different from `pve-d1`’s physical NIC MAC, even though it is using the same physical network through Proxmox’s Linux bridge.

---

# Storage Setup

On `pve-d1`, the 256 GB Samsung SSD was added and configured through the Proxmox GUI as LVM-thin storage.

Current result on D1:

```text
d1-ssd-lvm
Type: LVM-thin
Size: about 244.93 GB
Usage: 0%
Purpose: VM disks / container root disks
```

This was done correctly.

The boot SSD on D1 is:

```text
sdb: 128 GB Toshiba SSD
Contains Proxmox root, swap, local-lvm
```

The extra Samsung SSD is:

```text
sda: 232.9 GB Samsung SSD 850 EVO
Configured as d1-ssd-lvm
```

Important storage concept:

A disk showing under **Disks** does not automatically show under **Directory** or as VM storage. It must be initialized and added as storage, for example Directory, LVM, LVM-thin, ZFS, etc.

For VM storage, LVM-thin is good because it supports VM disks efficiently and integrates well with Proxmox.

---

# Monitoring Stack

I created a monitoring LXC container:

```text
CT ID: 201
Name: monitoring
Location: pve-6420
```

The monitoring container runs Docker and Docker Compose.

Monitoring stack includes:

```text
Prometheus
Grafana
Alertmanager
Proxmox VE Exporter
Node Exporter installed on Proxmox nodes
```

Node Exporter was installed directly on Proxmox nodes and confirmed working on port:

```text
9100
```

Example check:

```bash
curl http://10.44.0.50:9100/metrics | head
```

The `curl: (23) Failure writing output to destination` message after piping to `head` is normal because `head` closes the pipe early.

Prometheus and Grafana are running inside Docker in the monitoring LXC.

Ports:

```text
Grafana:       http://10.44.0.80:3000
Prometheus:    http://10.44.0.80:9090
Alertmanager:  http://10.44.0.80:9093
PVE Exporter:  http://10.44.0.80:9221
```

Important note about PVE exporter:

Opening:

```text
http://10.44.0.80:9221
```

shows:

```text
Visit /pve?target=1.2.3.4 to use.
```

That is normal. The exporter is not a dashboard. Prometheus calls it with a target parameter.

Prometheus targets are working, and I installed/imported a Node Exporter dashboard. I also created/customized a basic homelab Grafana dashboard for:

```text
Node up/down
CPU usage by node
RAM usage by node
Disk usage by node
Network receive/transmit
Load average
Proxmox VM/LXC count
VM/LXC CPU usage
VM/LXC RAM usage
Storage overview
Cluster node status
```

Future monitoring expansion plan:

```text
Phase 1: Prometheus + Grafana
Phase 2: Add Loki for logs
Phase 3: Add Tempo for traces if needed
No Mimir
```

---

# Users and Permissions

There are several different kinds of users, and this was a source of confusion.

## Proxmox users

Visible under:

```text
Datacenter > Permissions > Users
```

Current Proxmox GUI users include:

```text
root@pam
prometheus@pve
```

Explanation:

```text
root@pam
```

This is the Linux root user from the Proxmox host, authenticated through PAM. It is the main admin login for Proxmox.

```text
prometheus@pve
```

This is a Proxmox internal user created for the Proxmox VE exporter. It is not a Linux shell user. It is used so Prometheus/PVE exporter can read Proxmox API metrics.

## Linux users inside containers/VMs

These are separate from Proxmox users.

Examples:

```text
admin
sam
root
```

The `admin` user was created inside the monitoring LXC. It is a Linux user inside that container, not a Proxmox datacenter user.

The `sam` user was created inside the Ubuntu `llm-gpu` VM. It is a Linux user inside that VM, not a Proxmox datacenter user.

Important concept:

```text
Proxmox GUI users control access to the Proxmox web UI/API.
Linux users inside VMs/LXCs control login/sudo inside that guest system.
They are separate.
```

---

# LLM GPU VM

I created an Ubuntu VM on `pve-d1` for local LLM testing.

VM:

```text
VM ID: 301
Name: llm-gpu
Host: pve-d1
OS: Ubuntu 24.04.3 LTS
Purpose: Local LLM server with NVIDIA GPU passthrough
```

VM storage:

```text
Storage: d1-ssd-lvm
Disk size: 160 GB
```

VM CPU/RAM plan:

```text
CPU: several cores from i7-4790, likely 6 vCPU is reasonable
RAM: around 20 to 24 GB recommended
GPU: NVIDIA GTX 1070 passed through
```

VM network:

```text
Uses VirtIO network device
Gets its own MAC address
Connected through Proxmox bridge to LAN
```

The NVIDIA driver is working inside the VM.

`nvidia-smi` showed:

```text
Driver Version: 580.159.03
CUDA Version: 13.0
GPU: NVIDIA GeForce GTX 1070
VRAM: 8192 MiB
```

---
# Future AI Harness Plan

The long-term AI setup should be separated like this:

```text
D1 / llm-gpu VM
Runs local models through llama.cpp server using GTX 1070

Separate agent harness VM or LXC
Runs OpenClaw / Hermes / Codex-based orchestration
Calls local llama.cpp server over HTTP

Storage node
Stores models, backups, Obsidian vault copies, RAG data, shared files

Monitoring LXC
Prometheus + Grafana + exporters
```

Main brain:

```text
Codex
```

Local helper model:

```text
llama.cpp server on llm-gpu using GTX 1070
```

Potential local models:

```text
llama3.1 8B Q4_K_M
qwen3.5 4B
gemma3 4B
qwen2.5-coder 7B
```

Qwen 9B may be too large for full GPU use on the GTX 1070.


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