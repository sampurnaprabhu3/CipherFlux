# CipherFlux

### AI-Powered Intrusion Detection and Response System for Critical Infrastructure

---

## Overview

CipherFlux is a real-time intrusion detection system built for critical infrastructure — Oil & Gas SCADA networks, Healthcare, Financial Services, Smart Manufacturing, and Enterprise IT.

It captures live network packets, detects threats using dual ML models trained on real SCADA/ICS traffic, and autonomously investigates and responds to incidents using a 4-agent CrewAI pipeline powered by a locally running Llama 3 model — entirely on-device, no cloud required.

---

## Key Features

- Real-time packet capture via Scapy + Npcap
- Dual ML detection — Random Forest (~100% accuracy) + Isolation Forest (~98.83% accuracy)
- 4-agent CrewAI pipeline — Threat Investigator → Decision Maker → Response Executor → Report Generator
- Local LLM (Llama 3 via Ollama) — fully offline, no API keys needed
- Live Streamlit dashboard — alerts, severity chart, blocked IPs, sector config
- 5 sector profiles — Oil & Gas, Healthcare, Finance, Manufacturing, Enterprise IT
- No Docker, no cloud — runs on a standard Windows laptop

---

## Tech Stack

| Technology | Role |
|---|---|
| Python 3.10+ | Core language |
| Scapy + Npcap | Live packet capture |
| Random Forest | Known attack classification |
| Isolation Forest | Novel anomaly detection |
| CrewAI | Multi-agent orchestration |
| Llama 3 (Ollama) | Local LLM for investigation + reporting |
| Streamlit | Live dashboard |
| SQLite | Packet, alert, and report storage |

---

## ML Models

| Model | Accuracy | Purpose |
|---|---|---|
| Random Forest | ~100% | Classify known attacks (DoS, Probe, Exploit, Recon) |
| Isolation Forest | ~98.83% | Detect novel anomalies, assign severity (Low → Critical) |

Training data: UNSW NB15 (2.5M real network traffic records) + ICS-specific Modbus/DNP3 captures

---

## System Architecture

```
Network Traffic
      ↓
Scapy + Npcap (loopback capture)
      ↓
21-Feature Extraction + MinMaxScaler
      ↓
Random Forest + Isolation Forest
      ↓ Threat detected
CrewAI Agent Pipeline
  1. Threat Investigator
  2. Security Decision Maker
  3. Response Executor
  4. Report Generator (Llama 3)
      ↓
SQLite DB + Streamlit Dashboard
```


## My Role

Led the team as project lead for our final year B.Tech project (Information Technology, Vidyalankar Institute of Technology, 2025–26). Responsible for system architecture, agentic pipeline design, ML model selection and integration, and overall product direction.


---

## Future Scope

- Deep packet inspection for Modbus, DNP3, S7Comm
- GPU-accelerated Llama 3 inference
- MITRE ATT&CK for ICS tactic mapping
- Mobile monitoring dashboard
- Extended sectors: Water, Transportation, Telecom
