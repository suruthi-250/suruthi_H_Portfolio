# PHISH-001 — Chase Bank Account Suspension Phishing Investigation

## Overview

This project documents the investigation of a phishing email impersonating **Chase Bank** and claiming that the recipient's account had been temporarily suspended due to unusual activity.

The investigation used email header analysis, authentication results, sender infrastructure analysis, URL analysis, IOC extraction, and social-engineering assessment to determine the legitimacy of the message.

**Verdict:** Malicious — Phishing / Credential Harvesting Attempt
**Confidence:** High
**Date Analyzed:** July 2026
**Sample ID:** PHISH-001

> **Note:** The sample was sourced from TCM Security's SOC 101 course materials and used for personal practice.

---

## Objective

The objective of this investigation was to determine whether the email was a legitimate Chase communication or a phishing attempt by analyzing:

* Email metadata and headers
* Sender authentication results
* Received mail infrastructure
* Reply-To and Return-Path information
* Embedded URLs
* Indicators of compromise
* Social-engineering techniques
* Relevant MITRE ATT&CK techniques

---

## Investigation Methodology

The investigation followed a structured email-analysis process:

1. **Email Metadata Analysis**

   * Reviewed the subject, display sender, Reply-To, Return-Path, and timestamps.

2. **Header Analysis**

   * Examined SPF, DKIM, and DMARC results.
   * Traced the Received chain to identify the originating infrastructure.
   * Compared the claimed sender identity with the actual sending infrastructure.

3. **Infrastructure Analysis**

   * Identified the actual ProtonMail sending infrastructure.
   * Investigated the originating IP and sender domains.
   * Looked for inconsistencies between the claimed Chase identity and the technical infrastructure.

4. **URL Analysis**

   * Examined the embedded shortened URL.
   * Used URL analysis and reputation services to assess the destination.
   * Considered the possibility that the original phishing destination was no longer active.

5. **IOC Extraction**

   * Documented relevant domains, IP addresses, email addresses, URLs, and hosted resources.

6. **Social-Engineering Analysis**

   * Examined urgency, brand impersonation, generic wording, spelling errors, and the account-suspension pretext.

---

## Key Findings

### Sender Identity Mismatch

The visible sender claimed to be:

`alerts@chase.com`

However, the actual sending infrastructure was associated with **ProtonMail**, including `mail-40140.protonmail.ch` and the sender IP `185.70.40.140`. The Reply-To and Return-Path also pointed to a ProtonMail address rather than Chase infrastructure.

### Authentication Analysis

The message produced:

* **SPF:** Pass — aligned with protonmail.com
* **DKIM:** Timeout
* **DMARC:** Pass — aligned with protonmail.com

The authentication results therefore reflected the attacker's actual ProtonMail domain rather than authorization from Chase.

### Received Chain

The Received chain showed the message originating from ProtonMail infrastructure before being delivered through Microsoft mail infrastructure. No Chase infrastructure was identified in the chain.

### URL Analysis

The email contained a shortened URL using `dsgo.to`. Analysis showed that the URL currently resolved to the shortener's homepage rather than an active phishing page.

This was treated as consistent with an expired campaign rather than evidence that the original link was legitimate. The report assessed the intended destination as likely being a Chase-branded credential-harvesting page based on the email's pretext and other indicators.

### Social-Engineering Indicators

The investigation identified several social-engineering indicators:

* Account-suspension pretext
* Urgency and fear
* Chase brand impersonation
* Generic greeting
* Spelling error
* Generic sign-off

These elements were designed to pressure the recipient into taking immediate action.

---

## Indicators of Compromise

| Type            | Indicator                       | Description                                |
| --------------- | ------------------------------- | ------------------------------------------ |
| Spoofed Display | `alerts@chase.com`              | Chase brand impersonation                  |
| Reply-To        | `kellyellin426@proton.me`       | Attacker infrastructure                    |
| Originating IP  | `185.70.40.140`                 | ProtonMail infrastructure                  |
| URL             | `hxxps://dsgo.to/...`           | Shortened URL associated with the campaign |
| Hosting         | `raw.githubusercontent.com/...` | Hosted phishing branding asset             |

---

## MITRE ATT&CK Mapping

* **T1566.002 — Phishing: Spearphishing Link**
* **T1204.001 — User Execution: Malicious Link**

---

## Verdict

**Malicious — Phishing / Credential Harvesting Attempt**

**Confidence: High**

The conclusion was based on the combination of:

* Sender infrastructure mismatch
* ProtonMail Reply-To and Return-Path
* Inconsistent claimed sender identity
* Suspicious shortened URL
* Account-suspension social-engineering pretext
* Brand impersonation
* Additional header and content anomalies

The SPF and DMARC passes did not establish that the message was authorized by Chase; they reflected alignment with the attacker's ProtonMail domain.

---

## Recommended Actions

The investigation recommended:

* Blocking the identified sender infrastructure where appropriate
* Blocking the suspicious URL
* Searching mail logs for additional recipients
* Submitting identified IOCs to threat-intelligence systems
* Reviewing spam-filter tuning for financial-brand impersonation
* Providing security-awareness guidance to affected users
* Developing detection logic for financial-brand display names combined with consumer webmail sending domains

---

## Full Report

[**View Full Investigation Report**](sample1.eml.docx)

---

## Evidence

Supporting screenshots from the investigation are available in the `Screenshots/` directory.

```text
PHISH-001/
├── README.md
├── Report.docx
└── Screenshots/
```

---

## Skills Demonstrated

* Email Header Analysis
* SPF / DKIM / DMARC Analysis
* Email Infrastructure Analysis
* Phishing Investigation
* IOC Extraction
* URL Analysis
* Social-Engineering Analysis
* Threat Analysis
* MITRE ATT&CK Mapping
* Security Recommendations
