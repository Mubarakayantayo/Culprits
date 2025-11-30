# Milestone 3 — Progress Report

## Project Title
**LLM-Integrated Honeypot for Intelligent Threat Deception**

## Team Members
- Mubarak Ayantayo  
- Jack Wehberg

## Project Type
**Option C — Combination:** A 3-page research paper + software implementation

---

## 1 Project Overview

This project deploys an **AI-augmented honeypot** using the `Beelzebub` framework by integrating a Large Language Model (LLM), such as `GPT-4o` or offline `Ollama` models, into a containerized deception environment.

The system simulates realistic terminal exploitation behavior, deceiving attackers into believing they are interacting with a legitimate Linux system. Attacker activity is logged, captured, and analyzed in real-time using an `ELK Stack` monitoring dashboard.

---

## Security Problem Addressed

Traditional honeypots rely on static, predictable responses that attackers can recognize easily. As a result:

- Deception quickly fails  
- Most captured activity is low-value (e.g., port scans)  
- Behavioral insight is limited  

This project aims to introduce **high-interaction intelligent deception** by leveraging LLMs to generate dynamic responses, increasing attacker engagement time and capturing advanced intrusion behaviors.

The honeypot VM remains publicly accessible for extended durations to collect data and compare traditional honeypots with LLM-based deception results.

---

## 2 Current Progress

---

### 2.1 Completed Work

#### Honeypot Frameworks & Research
- Beelzebub honeypot low code YAML configurations, multi-protocol deception, and simulation of system interactions. Its git documentation, static analysis tooling (CodeQL, Go Report Card), and ELK dashboard
- T-Pot honeypot setup and studied the 20+ honeypot modules (Cowrie, Suricata, RedisHoney, ADBHoney, Mailoney, etc.) just to understand attacker behaviors
- ELK (Elasticsearch, Logstash, Kibana) for primary monitoring and analytics backend.
- Prompt injection from youtube videos on guardrail bypass, malicious input activation, and AI-targeted attack vectors

---

### VM Infrastructure Setup

- Created Azure: Virtual network, NSG with restricted access, resource group, and subnets to deploy Ubuntu 24.04 VM using B-series sizing.
- Installed and configured T-Pot honeypot suite and expand VM disk capacity and configured safe
container-level isolation.
- Verified HTTPS dashboard access on port.

---

### Data Collection & Analysis

The honeypot has collected large-scale attacker telemetry:

**Top honeypots hit:**
- DDoSpot (~26K)
- Cowrie (~20K)
- Dionea (~18K)
- Honeytrap (~17K)

**Top source countries:**
- Indonesia
- USA
- China
- Hong Kong
- UK

**Observed attacks:**
- Web attacks (Tanner): /, /.env, /wp-admin.php, and exploit-encoded paths.
- Redis attacks (Redishoney): INFO, PING, invalid commands, new connections.
- SMTP data (Mailoney): repeated sender/receiver spoofing attempts.
- Cowrie logs: Over 10,000 SSH brute force attempts from 71.66.180.6, including password spray attempts and a captured file.
- ADBHoney malware: 10 hashes through VirusTotal, mostly Mirai/Bashlite variants.

---

### Prototype for future Progress

- Test Beelzebub locally via Docker and review its modular service configuration
- Successfully build custom LLM-powered SSH honeypot configs using:- Configured LLM-based SSH deception using:
  - `GPT-4o` (OpenAI)
  - `Llama-based models` via Ollama
- Write an initial LLM prompt template that forces the model to behave as a Linux terminal.
- View ELK analysis.

---

### 2.2 Tools & Technologies

#### Languages/Frameworks:
- Go (Beelzebub)
- Python
- YAML

#### Honeypot Frameworks
- Beelzebub
- T-Pot (Cowrie, Suricata, RedisHoney, ADBHoney, Mailoney)

#### Infrastructure
- Azure VM (Ubuntu 24.04)
- Docker & Docker Compose

#### AI Systems
- GPT-4o API
- Ollama-based LLMs

#### Analysis & Monitoring (ELK)
- Elasticsearch
- Logstash
- Kibana 

---

### Key Security Mechanisms Implemented / Analyzed

I’ll look into various security points like deception through LLM-generated terminal responses, container
sandboxing in VM. Network access restrictions in NSG rules. Credential-harvesting with Cowrie,
Heralding, RedisHoney, and Suricata to monitor network traffic for CVE-related exploits. Beelzebub’s
MCP creates an avenue for prompt-injection detection against AI agents, and ADBHoney collects
malware samples that are later classified with VirusTotal to identify botnet activity

---

### 2.3 ⚠️ Challenges Encountered

#### Technical Challenges
- At the moment none; just following instructions from past experience and researching more

#### Security Challenges
- The only thing I can think of is to prevent Beelzebub’s LLM from executing real commands on the host and crashing the VM..
#### Resource Limitations
- Not running out of Azure credits with increased ($100/year)
- VM storage and CPU usage spiking during Suricata + multiple honeypot modules.

#### Solutions & Workarounds
- We’ll be fine hopefully, We have 2 accounts we can use to capture data and any other student “.edu” account to create a new machine

---

## 3 Remaining Work & Timeline

---

### 3.1 Remaining Program Tasks

- Complete integration of Beelzebub honeypot onto the Azure VM.- Conduct comparative analysis:
- Analyze the results:
  - Session Length
  - Command Depth
  - Attacker persistence
  - Prompt injection attempts
- Compare the source of exploits to conventional port scans and password attempts.
---

### 3.2 Remaining Paper Tasks
- Write final Threat analysis for Beelzebub:

---

### 3.3 Combined Work

| Week | Goal |
|------|------|
| Next | Finish Beelzebub deployment + ELK pipeline and run the honeypot |
| Week 2 | Collect data & write paper |
| Week 3 | Create presentation |

---