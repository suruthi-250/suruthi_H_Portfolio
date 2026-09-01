# Lab Environment Setup

> **Purpose:** This document explains the home lab I use for phishing analysis, vulnerability simulations, and general SOC practice. I’m keeping the setup documented so I can reproduce my work and also show how I approach security safely.

---

## Overview

My lab is built around a single personal machine using virtual machines, local security tools, and a few online analysis services.

I’m keeping the environment relatively simple for now. The goal isn't to build a huge enterprise network — it's to have a safe environment where I can practice investigating security issues, analyzing suspicious emails, working with IOCs, and experimenting with security tools.

### A few principles I follow

* **Isolation:** I don't intentionally execute malicious samples on my host operating system.
* **Snapshots:** I take VM snapshots before experiments so I can return to a clean state.
* **Documentation:** I record the tools, commands, and steps I use during investigations.
* **Safe analysis:** Suspicious URLs and files are checked through appropriate analysis services rather than casually opened on my normal system.

---

## Hardware

My lab runs on a standard personal computer rather than dedicated server hardware.

| Component    | Specification                                                                  |
| ------------ | ------------------------------------------------------------------------------ |
| Host Machine | Personal laptop/workstation                                                    |
| RAM          | 16 GB                                                                          |
| Storage      | 256 GB SSD + external storage for VM files/snapshots                           |
| Network      | Home network with NAT; isolated VMs use Host-Only networking where appropriate |

The hardware is enough for my current work, although running several VMs at the same time can be resource-intensive.

---

## Host Operating System

**Host OS:** Windows

The host machine is mainly used for normal tasks such as browsing, managing files, taking notes, and working with my projects.

Security analysis is performed inside virtual machines whenever isolation is important. I avoid treating the host machine as the analysis environment for potentially dangerous files.

---

# Virtual Machines

## 1. Kali Linux — Primary Analysis VM

Kali Linux is currently the main environment I use for cybersecurity practice.

| Attribute  | Details                                                                  |
| ---------- | ------------------------------------------------------------------------ |
| Purpose    | Email analysis, header investigation, OSINT, networking tools, scripting |
| Base Image | Kali Linux                                                               |
| Network    | NAT for tasks requiring internet access; Host-Only for isolated testing  |
| Snapshots  | Clean baseline snapshot maintained for recovery                          |

### Tools I use

* `whois` — Domain and registration information
* `nslookup` / `dig` — DNS lookups
* `curl` / `wget` — Controlled HTTP requests and URL investigation
* **Python 3** — IOC extraction, automation, and small security scripts
* **Thunderbird** — Inspecting `.eml` files
* **Wireshark** — Network and packet analysis
* **Ghidra / radare2** — Exploring static analysis as I learn more about malware analysis

### Thunderbird configuration

When I inspect suspicious emails, I keep remote content disabled.

This is important because emails can contain externally hosted images, tracking pixels, or other content that may contact infrastructure controlled by an attacker.

I also avoid opening suspicious links directly from the email.

For investigations involving live infrastructure, I revert the VM to a known clean snapshot afterward.

---

## 2. Windows Analysis VM — Planned

I plan to add a separate Windows VM as I move further into endpoint and malware-analysis practice.

| Attribute  | Details                                                              |
| ---------- | -------------------------------------------------------------------- |
| Purpose    | Endpoint analysis, Windows artifacts, dynamic analysis practice      |
| Base Image | Windows 10/11                                                        |
| Network    | Host-Only or otherwise isolated during potentially risky experiments |
| Status     | Planned                                                              |

### Tools I want to explore

* **Sysmon** for Windows telemetry
* **Velociraptor / OSQuery** for endpoint artifact collection
* **FLARE VM** for Windows malware-analysis tooling

This VM isn't part of my current working environment yet, so I'm keeping it listed as a future addition rather than presenting it as something already deployed.

---

# Cloud & Web-Based Analysis

For certain investigations, I use online services to get additional context about URLs, files, domains, and IP addresses.

| Service        | How I use it                                                                  |
| -------------- | ----------------------------------------------------------------------------- |
| **VirusTotal** | File and URL reputation checks and comparing detections from multiple vendors |
| **URLScan.io** | Investigating suspicious URLs, redirects, and captured web pages              |
| **AbuseIPDB**  | Checking IP reputation and reported abuse                                     |
| **Any.Run**    | Planned for future sandbox-based dynamic analysis                             |

I don't rely on a single reputation service to decide whether something is malicious. The results are treated as one part of the investigation and are combined with other evidence such as headers, DNS information, URLs, timestamps, and observed behavior.

---

# Python Environment

**Python:** 3.11+

Python is becoming part of my regular cybersecurity workflow.

I currently use it for things such as:

* Parsing logs and text files
* Extracting indicators from email data
* Defanging and refanging IOCs
* Small automation scripts
* Generating or processing investigation data
* Dictionary attack simulations
* Recovery scripting in the AIG Log4j project

### Libraries I commonly use

* `requests` — Making HTTP/API requests where appropriate
* `re` — Extracting patterns such as URLs, IP addresses, and email addresses
* `json` / `csv` — Working with structured investigation data
* `datetime` — Working with timestamps and timelines

I don't store passwords, API keys, or other sensitive credentials in this repository.

---

# Email Analysis Workflow

Phishing and suspicious-email analysis is one of the areas I'm currently practicing the most.

My general workflow looks like this:

### 1. Obtain the sample

Samples come from educational exercises, authorized training platforms, or threat-intelligence sources.

### 2. Inspect the email safely

I open `.eml` files inside the Kali VM using Thunderbird, with remote content disabled.

I first look at the obvious indicators:

* Sender and display name
* Subject
* Message body
* Links
* Attachments
* Urgency or unusual requests

### 3. Inspect the raw message

I then move beyond the visible email and inspect the full headers.

Things I look for include:

* `Received` headers
* `Return-Path`
* `Message-ID`
* Sender IP
* Authentication results
* Sending domain
* URLs and domains contained in the message

### 4. Trace the email

I work through the `Received` chain to understand where the message actually came from rather than relying only on the sender name shown by the email client.

### 5. Extract IOCs

Depending on the sample, I collect:

* IP addresses
* Domains
* URLs
* Email addresses
* Message IDs
* File hashes
* Other useful indicators

### 6. Enrich the indicators

I use tools such as:

* WHOIS
* `nslookup`
* `dig`
* VirusTotal
* URLScan
* AbuseIPDB

The goal is to build enough context to make a reasonable assessment instead of declaring something malicious based on one indicator.

### 7. Defang indicators

IOCs are defanged before being included in public documentation.

For example:

`https://example.com/login`

becomes:

`hxxps://example[.]com/login`

This reduces the chance of someone accidentally clicking a malicious link from the repository.

### 8. Document the investigation

Finally, I record the evidence, my reasoning, the verdict, and recommended actions.

Where appropriate, I also map relevant behavior to **MITRE ATT&CK** techniques.

---

# Network Topology

The current setup is intentionally simple:

```text
                    ┌───────────────────────┐
                    │     Host Machine      │
                    │                       │
                    │ Browser / Files / IDE │
                    │ Notes / Git projects  │
                    └───────────┬───────────┘
                                │
                    ┌───────────┴───────────┐
                    │                       │
             ┌──────▼──────┐        ┌──────▼──────┐
             │ Kali Linux  │        │ Windows VM  │
             │     VM      │        │   Planned   │
             │             │        │             │
             │ Thunderbird │        │   Sysmon    │
             │ Python      │        │   Endpoint  │
             │ Wireshark   │        │   Analysis  │
             │ DNS/OSINT   │        │             │
             └──────┬──────┘        └─────────────┘
                    │
                    ▼
          ┌───────────────────────┐
          │ Online Analysis Tools │
          │                       │
          │ VirusTotal            │
          │ URLScan               │
          │ AbuseIPDB             │
          └───────────────────────┘
```

The Windows VM shown here is planned rather than currently deployed.

---

# Safety & Ethics

I'm using this lab for learning and authorized security practice.

My basic rules are:

* I don't intentionally execute malicious files on my host OS.
* I don't submit credentials to phishing pages.
* I use isolated environments when potentially risky analysis is necessary.
* I defang malicious URLs and other IOCs before putting them in public documentation.
* I don't use real victim information in my projects.
* My simulations come from authorized educational exercises or controlled scenarios.
* I don't attempt to access systems that I don't have permission to test.

If I encounter a real malicious campaign while doing research, the appropriate response is to document the evidence and use responsible reporting channels rather than attempting to interact with or disrupt the infrastructure.

---

# What's Next

The lab will grow as my skills develop.

| Planned Addition          | Why I want it                                                      |
| ------------------------- | ------------------------------------------------------------------ |
| **SIEM (Splunk / Wazuh)** | Practice log ingestion, alert investigation, and detection         |
| **Windows + Sysmon VM**   | Generate and investigate Windows endpoint telemetry                |
| **Active Directory Lab**  | Practice authentication, privilege, and lateral-movement detection |
| **Sigma Rules**           | Learn to write and test detection logic                            |
| **Zeek / Suricata**       | Practice network monitoring and PCAP-based investigation           |

I'm intentionally adding these gradually rather than setting up everything at once. The goal is to understand each component and actually use it in investigations.

---

# Reproducibility

Someone starting with a similar setup can reproduce the basic environment with:

1. Download Kali Linux from [kali.org](https://www.kali.org/).
2. Install Kali in VirtualBox or VMware.
3. Configure NAT for normal internet access and Host-Only networking when isolation is required.
4. Update the system:

```bash
sudo apt update
sudo apt full-upgrade
```

5. Install the tools needed for email and network analysis.
6. Configure Thunderbird so remote content is disabled.
7. Take a clean VM snapshot.
8. Create accounts for services such as VirusTotal and URLScan if needed.
9. Keep investigation samples and outputs organized in a dedicated lab directory.

I keep the setup simple enough that I can rebuild it if necessary. That's also useful practice for understanding how the tools actually work instead of depending on a preconfigured environment.

---

*Last updated: September 2026*

*This lab is used for personal learning, authorized simulations, and cybersecurity practice. Scenario materials belong to their respective owners; the analysis, scripts, and documentation in this repository are my own.*
