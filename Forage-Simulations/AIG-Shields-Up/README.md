# AIG — Shields Up: Cybersecurity Job Simulation

## Overview

Completed the **Shields Up: Cybersecurity** job simulation by **AIG through Forage** in August 2026.

The simulation provided practical exposure to vulnerability response, security advisory writing, and password-security concepts through scenario-based exercises.

**Provider:** Forage
**Organization:** AIG
**Completed:** August 26, 2026

---

## Practical Exercises

### 1. Log4Shell — CVE-2021-44228

The simulation included a zero-day vulnerability scenario based on **Log4Shell (CVE-2021-44228)**.

As part of the exercise, I:

* Researched the Log4j vulnerability
* Reviewed the CVE and relevant security advisories
* Identified affected software/version information
* Examined mitigation approaches
* Drafted an internal security advisory
* Considered the communication required when responding to a critical vulnerability

The exercise helped me understand how vulnerability response involves both **technical analysis and clear communication**.

CISA's guidance recommends updating affected Log4j deployments and provides additional mitigation measures where immediate upgrading is not possible.

---

### 2. Ransomware Scenario — Dictionary Attack

The second scenario involved a ransomware-related situation where an encrypted file needed to be recovered.

I wrote a Python script to perform a **dictionary attack** using a subset of the RockYou wordlist.

The script:

* Reads candidate passwords from a wordlist
* Attempts each password against an encrypted ZIP file
* Stops when the correct password is found
* Reports whether the password was successfully recovered

This exercise helped me understand the practical difference between a dictionary attack and a traditional brute-force approach, as well as the importance of password strength.

### Python Script

[**View `dictionary_attack.py`**](bruteforce.py)

---

## Skills Demonstrated

* Vulnerability Research
* CVE Analysis
* Security Advisory Analysis
* Vulnerability Management Concepts
* Incident Response Concepts
* Python Scripting
* Dictionary Attack Concepts
* Password Security
* Security Communication
* Technical Documentation

---

## Evidence

Screenshots from the simulation are included in the `Screenshots/` directory.

```text
AIG-Shields-Up/
├── README.md
├── Certificate.pdf
├── dictionary_attack.py
└── Screenshots/
```

---

## Certificate

[**View Certificate**](AIG-Shields-Up.pdf)

The certificate confirms completion of the **Shields Up: Cybersecurity Job Simulation** through Forage on August 26, 2026.

---

## Learning Resources

These resources were used to better understand the concepts covered during the simulation.

### Log4Shell / CVE-2021-44228

* [**Official CVE Record — CVE-2021-44228**](https://www.cve.org/CVERecord?id=CVE-2021-44228)
* [**CISA — Mitigating Log4Shell and Other Log4j-Related Vulnerabilities**](https://www.cisa.gov/news-events/cybersecurity-advisories/aa21-356a)
* [**CISA — Log4j Affected Software Database**](https://github.com/cisagov/log4j-affected-db)
* [**Log4Shell Overview — Wikipedia**](https://en.wikipedia.org/wiki/Log4Shell)

### Ransomware / Security Context

* [**CISA/FBI/NSA — Ransomware Trends 2021**](https://www.cisa.gov/news-events/news/cisa-fbi-nsa-and-international-partners-issue-advisory-ransomware-trends-2021)

These resources were used as learning references to understand the vulnerability, mitigation guidance, affected software, and broader security context. CISA's Log4j guidance specifically covers updating affected deployments and temporary mitigation measures.

---

## Note

This work was completed as part of an **externally provided Forage job simulation**. The exercises are documented here as practical learning experience and are not presented as an independently developed Log4j research project or security tool.
