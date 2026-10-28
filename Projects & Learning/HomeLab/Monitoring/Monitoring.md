# Monitoring

[[Projects & Learning/HomeLab/HomeLab Overview|HomeLab]] · [[Projects & Learning/Big Tasks|Big Tasks]]

## Goal

I want one view of cluster load, temperatures, and service health, plus useful benchmark/history features.

## Current setup

Grafana, Prometheus, Alertmanager, and the Proxmox exporter run in LXC 201 on pve-6420. Node exporters run on all five hosts. On 2026-10-27, the service checks responded and all 11 Prometheus targets were up.

Configuration and data locations: [[Projects & Learning/HomeLab/Homelab Setup/Configuration/Workloads and Services|Workloads and Services]]. Latest readings: [[Projects & Learning/HomeLab/Homelab Setup/Status|Status]].

## Reconfiguration direction

I want a dashboard with per-node load and statistics, plus homelab-wide totals for RAM, CPU/core capacity, and storage usage. Reconfiguring the existing stack or changing it are both open options; a replacement has not been chosen. Confirmed 2026-10-27.

## Desired features

- CPU and RAM load for every node, plus D1 GPU utilization.
- Homelab-wide RAM, CPU/core capacity, and storage usage totals alongside the per-node view.
- CPU/GPU and other available sensor temperatures.
- Simple network/CPU benchmarks from a button.
- Optional scheduled benchmarks with saved results and history, including network-speed trends.

Dashboard coverage, alerting settings, and benchmark choices are in [[Projects & Learning/HomeLab/Monitoring/Open Questions|Open Questions]].

## Connections

[[Projects & Learning/HomeLab/Node Issues/Node Issues|Node Issues]] needs incident evidence. [[Projects & Learning/HomeLab/Homelab Setup/Hardware/Node Inventory|Hardware]] supplies device details.

## Tasks

![[Projects & Learning/HomeLab/Monitoring/Tasks]]
