# Suricata IDS with Custom Detection Rules

A controlled Network Intrusion Detection System (NIDS) lab built using Suricata, EveBox, Kali Linux, and Ubuntu Linux.

The project demonstrates the creation and validation of custom Suricata detection rules for network reconnaissance, repeated SSH connection attempts, and SQL injection-style HTTP patterns.

---

## Project Overview

The main objectives of this project were to:

- Deploy and configure Suricata as a Network Intrusion Detection System
- Create custom Suricata detection rules
- Detect Nmap SYN reconnaissance
- Detect repeated SSH connection attempts
- Detect suspicious SQL injection-style HTTP requests
- Generate controlled network traffic using Kali Linux
- Validate alerts using Suricata logs
- Investigate alerts using EveBox
- Correlate IDS alerts with tcpdump traffic
- Map relevant activity to MITRE ATT&CK

All testing was performed in a controlled virtual laboratory environment.

---

## Lab Environment

| Component | Details |
|---|---|
| IDS | Suricata 7.0.3 |
| IDS Operating System | Ubuntu 24.04.5 LTS |
| IDS IP | 192.168.50.131 |
| Network Interface | ens33 |
| Testing Machine | Kali Linux |
| Kali IP | 192.168.50.128 |
| Alert Interface | EveBox 0.29.0 |
| EveBox Port | 5636 |
| Network Scanner | Nmap |
| Packet Analysis | tcpdump |
| Virtualization | VMware |

---

## Lab Architecture

```text
                    Controlled Test Traffic
                             │
                             ▼
                    ┌─────────────────┐
                    │   Kali Linux    │
                    │ 192.168.50.128  │
                    │                 │
                    │ Nmap / SSH /    │
                    │ HTTP Testing    │
                    └────────┬────────┘
                             │
                             │ Network Traffic
                             ▼
                    ┌─────────────────┐
                    │ Ubuntu +        │
                    │ Suricata IDS    │
                    │ 192.168.50.131  │
                    │ ens33            │
                    └────────┬────────┘
                             │
                    Custom Detection Rules
                             │
                  ┌──────────┴──────────┐
                  ▼                     ▼
             fast.log               eve.json
                                        │
                                        ▼
                                  ┌───────────┐
                                  │  EveBox   │
                                  │   :5636   │
                                  └─────┬─────┘
                                        │
                                        ▼
                                Alert Investigation