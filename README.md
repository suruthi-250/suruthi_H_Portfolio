# Suruthi H — Cybersecurity Portfolio

&gt; **Target Role:** SOC Analyst (Tier 1 / Junior)  
&gt; **Status:** Actively building — last updated September 2026

---

## About

Third-year Computer Science and Engineering student developing practical, hands-on cybersecurity skills aligned with Security Operations Center (SOC) responsibilities. This repository documents completed simulations, lab exercises, and independent analyses covering vulnerability response, phishing forensics, incident triage, and security awareness — with each project producing a written technical deliverable and extracted Indicators of Compromise (IOCs).

**Analytical approach:** Every conclusion is supported by raw headers, packet captures, reputation checks, or sandbox results. Assumptions are flagged, not presented as fact.

**Currently developing:** SIEM log analysis, detection engineering (Sigma rules), and Python automation for security workflows.

---

## Projects

| ID | Project | Category | Key Skills |
|:---|:---|:---|:---|
| [AIG-001](./vulnerability-management/aig-log4j-simulation) | AIG — Log4j Vulnerability Simulation | Vulnerability Management & Incident Recovery | CVE research, CISA advisory analysis, asset triage, patch prioritization, security advisory writing, Python scripting (dictionary attack simulation, ransomware recovery) |
| [MC-001](./security-awareness/mastercard-phishing-simulation) | Mastercard — Phishing Simulation | Security Awareness & Social Engineering | Phishing indicator analysis, employee-targeting scenario design, security training material development, risk communication |
| [PHISH-001](./phishing/PHISH-001-chase-bank) | Chase Bank Impersonation Phishing | Email Forensics & Threat Analysis | Header analysis, SPF/DKIM/DMARC interpretation, IOC extraction, URL reputation analysis (VirusTotal, URLScan, AbuseIPDB), MITRE ATT&CK mapping |
| [PHISH-002](./phishing/PHISH-002-cibc-bank) | CIBC Bank Account Suspension Phishing | Email Forensics & Threat Analysis | Advanced header tracing, typosquat detection, compromised relay analysis, "Franken-phish" template identification, multi-domain mismatch detection |
| [LEGIT-001](./phishing/LEGIT-001-namecheap) | Namecheap Domain Renewal — Benign Verification | Email Forensics & False-Positive Analysis | Authentication validation (SPF/DKIM/DMARC/ARC), legitimate ESP infrastructure verification, baseline comparison against phishing methodology |

*Table serves as the single source of truth. Updated as new projects are completed.*

---

## Skills Inventory

**Phishing & Email Forensics**
- Header analysis (Received chain tracing, Return-Path/Reply-To verification)
- Email authentication protocols: SPF, DKIM, DMARC, ARC
- IOC extraction and defanging/refanging
- OSINT & reputation analysis: VirusTotal, URLScan, AbuseIPDB, WHOIS, nslookup

**Vulnerability Management**
- CVE and CISA advisory research and interpretation
- Asset identification and patch prioritization
- Security advisory writing (technical and executive audiences)
- Python scripting for security automation and recovery

**Incident Response Fundamentals**
- Evidence collection and chain-of-custody documentation
- Containment and mitigation reasoning
- Timeline reconstruction from logs and headers

**Security Awareness & Communication**
- Phishing indicator recognition and social engineering tactic identification
- Employee training material design
- Audience-appropriate security reporting (technical detail vs. executive summary)

**Frameworks & Methodologies**
- MITRE ATT&CK technique mapping
- Structured analytical approach: observed facts → analysis → conclusion → recommendation

**Scripting & Tools**
- Python (file handling, log parsing, basic security tooling)
- Kali Linux command-line tools (whois, nslookup, dig)
- Email client forensics (Thunderbird, raw .eml inspection)

---

## Why SOC?

A SOC analyst operates at the intersection of technical depth and clear communication — two areas this portfolio deliberately pairs in every project. Whether analyzing a suspicious email header or writing a post-incident advisory, the goal is the same: transform raw evidence into actionable intelligence that protects the organization.

---

## Connect

- **LinkedIn:** https://www.linkedin.com/in/suruthi-h/


---

## Attribution & License

All analysis, code, written reports, and IOC extractions in this repository are original work by the author. Scenario materials and sample emails are sourced from educational platforms (TCM Security SOC 101, Forage) and belong to their respective sponsors. This portfolio is maintained for educational and professional demonstration purposes only.

---

*Last updated: September 2026*
