

# Quick Access

```bash
ssh sam@llm-gpu
ssh root@pve-d1
cd /home/sam/services/career-ops
```

# SSH Access

## LLM-GPU With Tailscale

```bash
ssh sam@llm-gpu
ssh sam@<LLM_GPU_TAILSCALE_IP>
```

## LLM-GPU on Local Network

```bash
ssh sam@10.44.0.170
```

## Proxmox With Tailscale

```bash
ssh root@pve-d1
ssh root@<PROXMOX_TAILSCALE_IP>
```

## Proxmox on Local Network

```bash
ssh root@<PROXMOX_LAN_IP>
```

## Without Tailscale While Away

Requires router port forwarding:

```bash
ssh -p 2222 sam@<PUBLIC_IP>
```

## Verbose SSH Troubleshooting

```bash
ssh -v sam@llm-gpu
ssh -vvv sam@llm-gpu
```

# SSH Aliases

## Edit SSH Configuration

```bash
nano ~/.ssh/config
```

```sshconfig
Host llm-gpu
    HostName llm-gpu
    User sam
    ServerAliveInterval 30
    ServerAliveCountMax 6

Host llm-gpu-lan
    HostName 10.44.0.170
    User sam

Host proxmox
    HostName pve-d1
    User root
    ServerAliveInterval 30
    ServerAliveCountMax 6

Host llm-gpu-public
    HostName <PUBLIC_IP>
    User sam
    Port 2222
    ServerAliveInterval 30
    ServerAliveCountMax 6
```

```bash
chmod 600 ~/.ssh/config
```

## Use Aliases

```bash
ssh llm-gpu
ssh llm-gpu-lan
ssh proxmox
ssh llm-gpu-public
```

# SSH Keys

## Generate a Key

```bash
ssh-keygen -t ed25519 -C "sam"
```

## Copy Key to LLM-GPU

```bash
ssh-copy-id sam@llm-gpu
ssh-copy-id sam@10.44.0.170
```

## Test Key Authentication

```bash
ssh sam@llm-gpu
```

# File Transfer

## Computer to LLM-GPU With Tailscale

```bash
scp <FILE> sam@llm-gpu:~/
scp -r <FOLDER> sam@llm-gpu:~/
```

## LLM-GPU to Computer With Tailscale

```bash
scp sam@llm-gpu:/path/to/file .
scp -r sam@llm-gpu:/path/to/folder .
```

## Computer to LLM-GPU on Local Network

```bash
scp <FILE> sam@10.44.0.170:~/
scp -r <FOLDER> sam@10.44.0.170:~/
```

## LLM-GPU to Computer on Local Network

```bash
scp sam@10.44.0.170:/path/to/file .
scp -r sam@10.44.0.170:/path/to/folder .
```

## Transfer Using SSH Alias

```bash
scp <FILE> llm-gpu:~/
scp -r <FOLDER> llm-gpu:~/
scp llm-gpu:/path/to/file .
scp -r llm-gpu:/path/to/folder .
```

## Transfer Using Public IP

```bash
scp -P 2222 <FILE> sam@<PUBLIC_IP>:~/
scp -P 2222 sam@<PUBLIC_IP>:/path/to/file .
```

## Transfer With Progress and Resume

### Computer to LLM-GPU

```bash
rsync -avhP <FILE> sam@llm-gpu:/path/to/destination/
rsync -avhP <FOLDER>/ sam@llm-gpu:/path/to/destination/
```

### LLM-GPU to Computer

```bash
rsync -avhP sam@llm-gpu:/path/to/file .
rsync -avhP sam@llm-gpu:/path/to/folder/ ./folder/
```

### Using Public SSH Port

```bash
rsync -avhP -e "ssh -p 2222" <FILE_OR_FOLDER> sam@<PUBLIC_IP>:/path/to/destination/
```

## Upload Voice Memo

```bash
scp "<RECORDING>.m4a" sam@llm-gpu:~/private-transcription/audio/
```

## Download Transcription Results

```bash
scp -r sam@llm-gpu:~/private-transcription/output/ .
```

# Tailscale Installation

## Install on LLM-GPU

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo systemctl enable --now tailscaled
sudo tailscale up --hostname=llm-gpu
```

## Install on Proxmox

Run as `root`:

```bash
curl -fsSL https://tailscale.com/install.sh | sh
systemctl enable --now tailscaled
tailscale up --hostname=pve-d1 --accept-dns=false
```

# Tailscale Commands

## Status and IP

```bash
tailscale status
tailscale ip
tailscale ip -4
tailscale version
```

## Test Connectivity

```bash
tailscale ping llm-gpu
tailscale ping pve-d1
tailscale netcheck
```

## Connect and Disconnect

```bash
sudo tailscale up
sudo tailscale down
```

## Change Hostname

```bash
sudo tailscale set --hostname=llm-gpu
```

## Enable Tailscale SSH

```bash
sudo tailscale set --ssh
```

## Disable Tailscale SSH

```bash
sudo tailscale set --ssh=false
```

## Restart Tailscale

```bash
sudo systemctl restart tailscaled
sudo systemctl status tailscaled --no-pager
```

## Tailscale Logs

```bash
journalctl -u tailscaled -n 100 --no-pager
journalctl -u tailscaled -f
```

## Log Out Device

```bash
sudo tailscale logout
```

# Proxmox Access

## Web Interface With Tailscale

```text
https://pve-d1:8006
```

## Web Interface With LAN IP

```text
https://<PROXMOX_LAN_IP>:8006
```

# Career-Ops

## Open Career-Ops

```bash
ssh llm-gpu
cd /home/sam/services/career-ops
```

## Check Repository

```bash
pwd
git status
git log --oneline -10
npm run
```

## Install Dependencies

```bash
npm install
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

## Query and Triage Jobs

```bash
node tracker.mjs query
```

## View Pipeline

```bash
sed -n '1,260p' data/pipeline.md
```

## View Scan History

```bash
tail -n 40 data/scan-history.tsv
tail -n 20 data/scan-runs.tsv
```

## View Reports

```bash
find reports -maxdepth 2 -type f | sort | tail -n 30
```

## Follow Scan Log

```bash
tail -f /home/sam/services/career-ops/data/systemd-scan.log
```

## Follow Discovery Log

```bash
tail -f /home/sam/services/career-ops/data/systemd-discovery.log
```

# Career-Ops Scheduled Scans

## Check All Career-Ops Timers

```bash
systemctl --user list-timers --all | grep careerops
```

## Scan Timer Status

```bash
systemctl --user status careerops-scan.timer --no-pager
```

## Last Scan Status

```bash
systemctl --user status careerops-scan.service --no-pager
```

## Scan Logs

```bash
tail -n 100 /home/sam/services/career-ops/data/systemd-scan.log
journalctl --user -u careerops-scan.service -n 100 --no-pager
```

## Follow Scan Logs

```bash
journalctl --user -u careerops-scan.service -f
```

## Run Scan Now

```bash
systemctl --user start careerops-scan.service
```

## Enable Scheduled Scans

```bash
systemctl --user daemon-reload
systemctl --user enable --now careerops-scan.timer
```

## Restart Scan Timer

```bash
systemctl --user restart careerops-scan.timer
```

## Stop Scan Timer

```bash
systemctl --user stop careerops-scan.timer
```

# Career-Ops Scheduled Discovery and Triage

## Discovery Timer Status

```bash
systemctl --user status careerops-discovery.timer --no-pager
```

## Last Discovery Status

```bash
systemctl --user status careerops-discovery.service --no-pager
```

## Discovery Logs

```bash
tail -n 100 /home/sam/services/career-ops/data/systemd-discovery.log
journalctl --user -u careerops-discovery.service -n 100 --no-pager
```

## Follow Discovery Logs

```bash
journalctl --user -u careerops-discovery.service -f
```

## Run Discovery Now

```bash
systemctl --user start careerops-discovery.service
```

## Enable Scheduled Discovery

```bash
systemctl --user daemon-reload
systemctl --user enable --now careerops-discovery.timer
```

## Restart Discovery Timer

```bash
systemctl --user restart careerops-discovery.timer
```

## Stop Discovery Timer

```bash
systemctl --user stop careerops-discovery.timer
```

## Restart Both Timers

```bash
systemctl --user restart careerops-scan.timer careerops-discovery.timer
```

## Stop Both Timers

```bash
systemctl --user stop careerops-scan.timer careerops-discovery.timer
```

## Start Both Timers

```bash
systemctl --user start careerops-scan.timer careerops-discovery.timer
```

## Ensure User Timers Run While Logged Out

Check:

```bash
loginctl show-user sam -p Linger
```

Enable as root:

```bash
sudo loginctl enable-linger sam
```

# System Services

## Check a Service

```bash
systemctl status <SERVICE> --no-pager
systemctl is-active <SERVICE>
systemctl is-enabled <SERVICE>
```

## Start, Stop and Restart

```bash
sudo systemctl start <SERVICE>
sudo systemctl stop <SERVICE>
sudo systemctl restart <SERVICE>
sudo systemctl reload <SERVICE>
```

## Enable or Disable at Boot

```bash
sudo systemctl enable <SERVICE>
sudo systemctl enable --now <SERVICE>
sudo systemctl disable <SERVICE>
```

## List Running Services

```bash
systemctl list-units --type=service --state=running
```

## List Failed Services

```bash
systemctl list-units --type=service --state=failed
systemctl --failed
```

## List All Installed Services

```bash
systemctl list-unit-files --type=service
```

## List User Services

```bash
systemctl --user list-units --type=service
systemctl --user list-unit-files --type=service
```

## Reload Service Definitions

```bash
sudo systemctl daemon-reload
systemctl --user daemon-reload
```

# Service Logs

## Recent Logs

```bash
journalctl -u <SERVICE> -n 100 --no-pager
journalctl --user -u <SERVICE> -n 100 --no-pager
```

## Follow Logs

```bash
journalctl -u <SERVICE> -f
journalctl --user -u <SERVICE> -f
```

## Logs Since Boot

```bash
journalctl -u <SERVICE> -b
```

## Logs Since a Specific Time

```bash
journalctl -u <SERVICE> --since "1 hour ago"
journalctl -u <SERVICE> --since today
```

## System Errors

```bash
journalctl -p err -b
```

# System Information

```bash
hostname
hostnamectl
lsb_release -a
uname -a
uptime
date
timedatectl
```

# CPU, Memory and GPU

## CPU

```bash
lscpu
nproc
```

## Memory

```bash
free -h
watch -n 2 free -h
```

## GPU

```bash
nvidia-smi
watch -n 1 nvidia-smi
nvidia-smi --query-gpu=name,temperature.gpu,utilization.gpu,memory.used,memory.total --format=csv
```

## CUDA Through Python

```bash
python3 -c "import torch; print(torch.cuda.is_available()); print(torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'No CUDA GPU')"
```

# Processes

## View Processes

```bash
ps aux
top
htop
```

## Find a Process

```bash
pgrep -af <PROCESS_NAME>
ps aux | grep <PROCESS_NAME>
```

## Process Using a Port

```bash
sudo lsof -i :<PORT>
sudo ss -lptn 'sport = :<PORT>'
```

## Stop a Process

```bash
kill <PID>
```

## Force Stop a Frozen Process

```bash
kill -9 <PID>
```

# Disk Usage

```bash
df -h
df -h /
du -sh *
du -sh <DIRECTORY>
du -h --max-depth=1 <DIRECTORY> | sort -h
lsblk
```

# Files and Directories

## Navigation

```bash
pwd
ls
ls -lah
cd <DIRECTORY>
cd ..
cd ~
```

## Create

```bash
mkdir <DIRECTORY>
mkdir -p <PARENT>/<CHILD>
touch <FILE>
```

## Copy and Move

```bash
cp <SOURCE> <DESTINATION>
cp -r <SOURCE_FOLDER> <DESTINATION>
mv <SOURCE> <DESTINATION>
```

## View Files

```bash
cat <FILE>
less <FILE>
head -n 20 <FILE>
tail -n 20 <FILE>
tail -f <FILE>
sed -n '1,200p' <FILE>
```

## Edit Files

```bash
nano <FILE>
vim <FILE>
```

## File Information

```bash
file <FILE>
stat <FILE>
ls -lh <FILE>
```

# Search

## Search File Contents

```bash
rg "SEARCH_TEXT"
rg "SEARCH_TEXT" <DIRECTORY>
rg -i "SEARCH_TEXT"
```

## Find Files

```bash
rg --files
rg --files | rg "<FILE_NAME>"
find . -name "<FILE_NAME>"
find . -type f | sort
```

## Find Recently Modified Files

```bash
find . -type f -mtime -1
```

# Permissions

## View Permissions

```bash
ls -lah
stat <FILE>
```

## Make Script Executable

```bash
chmod +x <SCRIPT>
```

## Secure SSH Configuration

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/config
chmod 600 ~/.ssh/authorized_keys
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
```

## Change Ownership

```bash
sudo chown <USER>:<GROUP> <FILE>
sudo chown -R <USER>:<GROUP> <DIRECTORY>
```

# Archives and Compression

## Create Tar Archive

```bash
tar -czf archive.tar.gz <FOLDER>
```

## Extract Tar Archive

```bash
tar -xzf archive.tar.gz
```

## Create ZIP Archive

```bash
zip -r archive.zip <FOLDER>
```

## Extract ZIP Archive

```bash
unzip archive.zip
```

# Checksums

```bash
sha256sum <FILE>
md5sum <FILE>
```

Compare the checksum on both machines after transferring a large file.

# Networking

## IP Addresses and Routes

```bash
ip addr
ip route
hostname -I
```

## Public IP

```bash
curl -4 ifconfig.me
```

## Connectivity

```bash
ping 1.1.1.1
ping google.com
curl -I https://example.com
```

## DNS

```bash
resolvectl status
getent hosts llm-gpu
nslookup <HOSTNAME>
```

## Open and Listening Ports

```bash
ss -tulpn
sudo ss -tulpn
sudo lsof -i -P -n
```

## Test a Port

```bash
nc -vz <HOST> <PORT>
```

## Network Interfaces

```bash
ip link
ethtool <INTERFACE>
```

# Git

## Repository Status

```bash
git status
git branch
git remote -v
```

## View History

```bash
git log --oneline -10
git log --oneline --graph --decorate --all
```

## View Changes

```bash
git diff
git diff --staged
```

## Update Repository

```bash
git fetch --all --prune
git pull
```

## Create Branch

```bash
git switch -c <BRANCH_NAME>
```

## Switch Branches

```bash
git switch <BRANCH_NAME>
```

## Stage and Commit

```bash
git add <FILE>
git add .
git commit -m "<MESSAGE>"
```

## Push

```bash
git push
git push -u origin <BRANCH_NAME>
```

## Temporarily Store Changes

```bash
git stash push -m "<MESSAGE>"
git stash list
git stash pop
```

## View a Specific Commit

```bash
git show <COMMIT>
```

## Compare Branches

```bash
git diff <BRANCH_ONE>..<BRANCH_TWO>
```

## Show Changed Files

```bash
git status --short
git diff --name-only
```

# Node and NPM

## Versions

```bash
node --version
npm --version
```

## Install Dependencies

```bash
npm install
npm ci
```

## List Available Scripts

```bash
npm run
```

## Run a Script

```bash
npm run <SCRIPT>
```

## Check Outdated Packages

```bash
npm outdated
```

# Python

## Version

```bash
python3 --version
pip3 --version
```

## Create Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## Leave Virtual Environment

```bash
deactivate
```

## Install Requirements

```bash
python3 -m pip install -r requirements.txt
```

## List Packages

```bash
python3 -m pip list
```

# Docker

## Status

```bash
docker version
docker info
docker ps
docker ps -a
```

## Images and Containers

```bash
docker images
docker logs <CONTAINER>
docker logs -f <CONTAINER>
docker inspect <CONTAINER>
```

## Start and Stop Container

```bash
docker start <CONTAINER>
docker stop <CONTAINER>
docker restart <CONTAINER>
```

## Docker Compose

```bash
docker compose ps
docker compose logs
docker compose logs -f
docker compose up -d
docker compose restart
docker compose down
```

## Resource Usage

```bash
docker stats
```

# Proxmox VM 301

## VM Status

```bash
qm status 301
```

## VM Configuration

```bash
qm config 301
```

## Start VM

```bash
qm start 301
```

## Graceful Shutdown

```bash
qm shutdown 301
```

## Restart VM

```bash
qm reboot 301
```

## Force Stop Frozen VM

```bash
qm stop 301
```

## List All VMs

```bash
qm list
```

## VM Console

```bash
qm terminal 301
```

# Background Sessions With tmux

## Start Session

```bash
tmux new -s <SESSION_NAME>
```

## Detach

```text
Ctrl+B, then D
```

## List Sessions

```bash
tmux ls
```

## Reconnect

```bash
tmux attach -t <SESSION_NAME>
```

## End Session

```bash
tmux kill-session -t <SESSION_NAME>
```

# Scheduled Tasks

## User Systemd Timers

```bash
systemctl --user list-timers --all
```

## System Timers

```bash
systemctl list-timers --all
```

## User Cron Jobs

```bash
crontab -l
```

## Root Cron Jobs

```bash
sudo crontab -l
```

# Package Management

## Update Package List

```bash
sudo apt update
```

## View Available Upgrades

```bash
apt list --upgradable
```

## Install Package

```bash
sudo apt install <PACKAGE>
```

## Find Package

```bash
apt search <PACKAGE>
```

# Reboot and Shutdown

## Reboot

```bash
sudo reboot
```

## Shutdown

```bash
sudo shutdown now
```

## Schedule Shutdown

```bash
sudo shutdown -h +10
```

## Cancel Scheduled Shutdown

```bash
sudo shutdown -c
```

# Quick Troubleshooting

## Server Unreachable

```bash
ping 10.44.0.170
tailscale ping llm-gpu
tailscale status
ssh -vvv sam@llm-gpu
```

## Career-Ops Did Not Run

```bash
systemctl --user list-timers --all | grep careerops
systemctl --user status careerops-scan.service --no-pager
systemctl --user status careerops-discovery.service --no-pager
journalctl --user -u careerops-scan.service -n 100 --no-pager
journalctl --user -u careerops-discovery.service -n 100 --no-pager
```

## Tailscale Is Down

```bash
sudo systemctl status tailscaled --no-pager
sudo systemctl restart tailscaled
sudo tailscale up
tailscale status
```

## GPU Is Not Detected

```bash
nvidia-smi
lsmod | rg nvidia
journalctl -k | rg -i "nvidia|cuda"
```

## Disk Is Full

```bash
df -h
du -h --max-depth=1 ~ | sort -h
journalctl --disk-usage
```

## Service Failed

```bash
systemctl status <SERVICE> --no-pager
journalctl -u <SERVICE> -n 100 --no-pager
systemctl --failed
```