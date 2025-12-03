# Milestone 3 — Progress Report

## Project Title
**LLM-Integrated Honeypot for Intelligent Threat Deception**

## Team Members
- Mubarak Ayantayo  
- Jack Wehberg

## Project Type
**Option C — Combination:** Research paper + software implementation

---

## 1. Project Overview

This project deploys a **real-world LLM-powered honeypot** using the Beelzebub framework inside a public Azure-hosted environment. The system integrates a locally hosted AI model (Ollama LLM) to simulate a fully interactive Linux environment for attackers.

Unlike traditional static honeypots, Beelzebub dynamically generates shell behavior using an LLM, allowing realistic deception, command interaction, and attacker engagement detection. All attacker interactions are streamed into an ELK stack (Elasticsearch, Logstash, Kibana) for real-time monitoring, session reconstruction, and behavioral analysis.

This environment is currently deployed on a publicly addressable VM and actively collecting live attacker telemetry.

---

## 2. Current Progress

---

## 2.1 Completed Work

### Full System Deployed

The following components are **fully operational**:

- Public Azure VM (Ubuntu 24.04)
- Docker-based Beelzebub deployment
- Ollama LLM backend (OpenChat model, custom prompt tuning)
- Multi-protocol deception services:
  - SSH (LLM interactive terminal)
  - Fake WordPress service
  - Apache 401 service
  - Fake MySQL
- ELK ingestion pipeline
- Beelzebub structured logging enabled

---

### AI Integration Completed

We implemented:

- A **custom LLM model profile** using Ollama (`tpot-llm`)
- Behavioral deception prompt injection into Beelzebub
- API-level LLM integration via Docker networking
- Session logging integrated into Elasticsearch

The LLM now responds dynamically to attacker input and produces simulated OS command execution output.

---

### Live Attacker Telemetry Observed

During deployment **within hours**, the honeypot began receiving attacks.

Captured logs include:

- Real IP sources
- Credential attempts
- Username/password brute force attempts
- Command execution probes
- Automated reconnaissance behaviors

Example artifacts collected:

- Usernames: `gerrit`, `hadoop`
- Passwords: `123456`, `password`, `1234567`, `passw0rd`
- Command attempts:
  - `uname`
  - `lscpu`
  - `/proc/uptime`
  - `.ssh enumeration`

Session examples logged:

- IP: `165.232.85.75`
- Multiple SSH sessions recorded
- State transitions logged (Start → End)
- Command execution traces saved as structured JSON

This confirms live exploitation traffic and validates real-world viability.

---

## 2.2 Tools & Technologies

### AI Stack
- Ollama LLM (OpenChat)
- Custom prompt injection + personal modeling

### Honeypot
- Beelzebub (LLM interactive SSH backend)

### Infrastructure
- Azure VM (Ubuntu 24.04 LTS)
- Docker & Docker Compose

### Logging & Analytics
- Elasticsearch
- Logstash
- Kibana

### Languages
- Go
- YAML
- Bash

---

## 2.3 Measured Attack Activity

### Attack Categories Observed

- SSH brute force
- Credential stuffing
- Environment fingerprinting
- OS reconnaissance
- Service identification probes

### Evidence Collected

- Structured logs per session
- Password dictionary patterns
- Multi-session automation from the same IP
- Command sequence reconstruction

---

## 2.4 Key Security Mechanisms Implemented

- LLM-driven terminal deception
- Container sandboxing
- Azure NSG filtering
- Prompt containment
- Credential harvesting
- Attack trace correlation
- Structured forensic logs
- Read-only file systems
- No live execution design

---

## 2.5 Challenges Encountered

### Infrastructure

- Docker port conflicts with existing honeypots
- IPv4/IPv6 binding conflicts
- API networking between host and container

### Solutions

- Custom port remapping
- Updated Docker networking config
- Local LLM host routing via `host.docker.internal`

### Security Challenges

- Preventing prompt-driven command execution
- Ensuring AI responses never reach host OS

All security issues were mitigated through container isolation and restricted permissions.

---

## 3. Remaining Work

---

## 3.1 System Analysis

Planned analysis features:

- Session duration (dwell time)
- Command entropy
- Brute-force patterns
- IP clustering
- Username/password frequency
- Attack automation signatures

---

## 3.2 Paper Work

The final paper will cover:

- AI deception vs static honeypots
- Attack realism comparison
- Behavioral analysis
- Ethical containment discussion
- Evasion resistance

---

## 3.3 Timeline

| Week          |------------ Deliverable---|
|---------------|---------------------------|
| Week 1        | Dashboard construction ---|
| Week 2.5 (Now)| Data analysis ------------|
| Week 3        | Paper + slides -----------|

---
