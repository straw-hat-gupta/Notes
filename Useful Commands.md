

## SSH With Tailscale

```bash
ssh sam@llm-gpu
ssh root@pve-d1
```

## SSH Without Tailscale

### Local Network

```bash
ssh sam@10.44.0.170
ssh root@<PROXMOX_LAN_IP>
```

### Away From Home

Requires router port forwarding:

```bash
ssh -p 2222 sam@<PUBLIC_IP>
```

## SSH Aliases

```bash
nano ~/.ssh/config
```


```bash
chmod 600 ~/.ssh/config

ssh llm-gpu
ssh llm-gpu-
ssh proxmox
```

# Tailscale

## Install on Proxmox or Debian/Ubuntu

```bash
curl -fsSL https://tailscale.com/install.sh | sh
systemctl enable --now tailscaled
tailscale up --hostname=pve-d1 --accept-dns=false
```

## Install on LLM-GPU

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo systemctl enable --now tailscaled
sudo tailscale up --hostname=llm-gpu
```

## Common Commands

```bash
tailscale status
tailscale ip -4
tailscale ping pve-d1
tailscale ping llm-gpu
sudo tailscale up
sudo tailscale down
sudo tailscale logout
sudo systemctl restart tailscaled
sudo systemctl status tailscaled
journalctl -u tailscaled -n 100 --no-pager
```

## Proxmox Web Interface

```text
https://pve-d1:8006
```

# Career-Ops

## Open Career-Ops

```bash
ssh llm-gpu
cd /home/sam/services/career-ops
```

## Full Scan

```bash
npm run scan -- --verify
```

## Verify Pipeline

```bash
node verify-pipeline.mjs
node cv-sync-check.mjs
```

## Sync Tracker

```bash
node tracker.mjs sync
```

## Triage Jobs

```bash
node tracker.mjs query
sed -n '1,260p' data/pipeline.md
```

## View Scan Results

```bash
sed -n '1,220p' data/pipeline.md
tail -n 40 data/scan-history.tsv
tail -n 20 data/scan-runs.tsv
find reports -maxdepth 2 -type f | sort | tail -n 30
```

# Scheduled Scans

## Check All Career-Ops Timers

```bash
systemctl --user list-timers --all | grep careerops
```

## Scan Status

```bash
systemctl --user status careerops-scan.timer --no-pager
systemctl --user status careerops-scan.service --no-pager
```

## Scan Logs

```bash
tail -n 100 /home/sam/services/career-ops/data/systemd-scan.log
journalctl --user -u careerops-scan.service -n 100 --no-pager
```

## Start Scan Schedule

```bash
systemctl --user daemon-reload
systemctl --user enable --now careerops-scan.timer
```

## Run Scan Now

```bash
systemctl --user start careerops-scan.service
```

# Scheduled Discovery and Triage

## Status

```bash
systemctl --user status careerops-discovery.timer --no-pager
systemctl --user status careerops-discovery.service --no-pager
```

## Logs

```bash
tail -n 100 /home/sam/services/career-ops/data/systemd-discovery.log
journalctl --user -u careerops-discovery.service -n 100 --no-pager
```

## Run Now

```bash
systemctl --user start careerops-discovery.service
```

## Restart Schedules

```bash
systemctl --user restart careerops-scan.timer
systemctl --user restart careerops-discovery.timer
```

## Stop Schedules

```bash
systemctl --user stop careerops-scan.timer careerops-discovery.timer
```

## Start Schedules

```bash
systemctl --user start careerops-scan.timer careerops-discovery.timer
```

# Proxmox VM 301

## Status

```bash
qm status 301
```

## Start

```bash
qm start 301
```

## Shutdown

```bash
qm shutdown 301
```

## Restart

```bash
qm reboot 301
```

## Configuration

```bash
qm config 301
```

## Enter VM Console

```bash
qm terminal 301
```

# LLM-GPU Status

```bash
hostnamectl
lsb_release -a
df -h /
free -h
nvidia-smi
uptime
```

## GPU Monitoring

```bash
watch -n 1 nvidia-smi
```

## Processes

```bash
ps aux
top
htop
```

## Services

```bash
systemctl status <SERVICE>
sudo systemctl restart <SERVICE>
journalctl -u <SERVICE> -n 100 --no-pager
```

# Files and Directories

```bash
pwd
ls -lah
cd <DIRECTORY>
mkdir <DIRECTORY>
cp <SOURCE> <DESTINATION>
mv <SOURCE> <DESTINATION>
nano <FILE>
less <FILE>
tail -f <FILE>
```

## Search

```bash
rg "SEARCH_TEXT"
rg --files
find . -name "<FILE_NAME>"
```

## Disk Usage

```bash
df -h
du -sh *
du -sh <DIRECTORY>
```

## Network

```bash
ip addr
ip route
hostname -I
ping 1.1.1.1
curl ifconfig.me
ss -tulpn
```

## Git

```bash
git status
git pull
git log --oneline -10
git branch
git diff
```

## Versions

```bash
git --version
node --version
npm --version
python3 --version
```