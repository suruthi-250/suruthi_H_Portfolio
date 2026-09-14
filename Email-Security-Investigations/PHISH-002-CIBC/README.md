# PHISH-002 — CIBC Bank Account Suspension Phishing Investigation

## Overview

This project documents the investigation of a phishing email impersonating **CIBC** and claiming that the recipient's account had been suspended due to unusual activity.

The investigation examined email headers, sender infrastructure, authentication results, domains, URLs, and social-engineering indicators to determine whether the message was legitimate or malicious.

**Verdict:** Malicious — Phishing / Credential Harvesting Attempt
**Confidence:** High
**Sample ID:** PHISH-002

> **Note:** The sample was used for cybersecurity investigation and analysis practice.

---

## Objective

The objective of this investigation was to determine whether the email was a legitimate CIBC communication or a phishing attempt by analyzing:

* Email metadata and headers
* Sender and recipient information
* SPF, DKIM, and DMARC results
* Received mail infrastructure
* Sender and Reply-To domains
* Domain similarity and possible typosquatting
* Embedded URLs
* Indicators of compromise
* Social-engineering techniques
* Relevant MITRE ATT&CK techniques

---

## Investigation Methodology

The investigation followed a structured email-analysis process:

1. **Email Metadata Analysis**

   * Reviewed the sender, recipient, subject, Reply-To, Return-Path, and message timestamps.

2. **Header Analysis**

   * Examined authentication results and the Received chain.
   * Traced the path through the identified mail infrastructure.
   * Compared the claimed CIBC identity with the actual sending infrastructure.

3. **Domain Analysis**

   * Examined the sender domain and identified a domain resembling the legitimate CIBC domain.
   * Investigated the possibility of typosquatting.

4. **URL Analysis**

   * Examined the embedded link and its destination.
   * Identified the `satole.com` domain associated with the phishing infrastructure.
   * Analyzed the URL and available reputation information.

5. **Content Analysis**

   * Examined the account-suspension message and its use of urgency and fear.
   * Compared the email's content and branding with legitimate CIBC communications.

6. **IOC Extraction**

   * Documented relevant domains, IP addresses, URLs, and email infrastructure associated with the investigation.

---

## Key Findings

### Sender Domain Typosquatting

The email used the domain:

`caib.com`

which closely resembles the legitimate CIBC domain:

`cibc.com`

This similarity can be used to create a deceptive sender identity and increase the likelihood that a recipient will mistake the email for a legitimate banking communication.

### Mail Infrastructure

Header analysis showed that the message passed through multiple mail relays, including infrastructure associated with **Comcast** and a **Honduran government mail server**.

The observed infrastructure did not establish a legitimate connection to CIBC.

### Authentication Analysis

The investigation examined the available SPF, DKIM, and DMARC results as part of determining whether the sender infrastructure was authorized and whether the claimed identity was trustworthy.

The authentication information was considered together with the sender domain, mail path, and other indicators rather than being treated as proof of legitimacy by itself.

### Malicious URL

The email contained a link associated with:

`satole.com`

The URL was identified as part of the phishing infrastructure and was assessed as leading toward a credential-harvesting page.

### Social-Engineering Indicators

The message used an account-suspension scenario designed to create urgency and encourage the recipient to interact with the provided link.

The investigation also identified similarities between the phishing message and a legitimate CIBC email template, suggesting that legitimate branding and content were being reused to make the message appear credible.

---

## Indicators of Compromise

| Type                | Indicator                     | Description                                   |
| ------------------- | ----------------------------- | --------------------------------------------- |
| Sender Domain       | `caib.com`                    | Domain resembling legitimate `cibc.com`       |
| Malicious Domain    | `satole.com`                  | Domain associated with the phishing URL       |
| URL                 | Phishing URL within the email | Credential-harvesting infrastructure          |
| Mail Infrastructure | Identified relay servers      | Infrastructure observed in the Received chain |

---

## MITRE ATT&CK Mapping

The investigation identified phishing-related techniques associated with the delivery of a malicious link and user interaction with the phishing content.

* **T1566.002 — Phishing: Spearphishing Link**
* **T1204.001 — User Execution: Malicious Link**

---

## Verdict

**Malicious — Phishing / Credential Harvesting Attempt**

**Confidence: High**

The conclusion was based on the combination of:

* CIBC impersonation
* Typosquatted sender domain
* Suspicious mail infrastructure
* Malicious URL
* Credential-harvesting destination
* Account-suspension social-engineering pretext
* Reuse of legitimate CIBC email content and branding

The individual technical indicators were evaluated together to establish the overall assessment.

---

## Recommended Actions

Recommended defensive actions include:

* Block identified malicious domains and URLs
* Search mail logs for additional recipients
* Identify and investigate other messages containing the same indicators
* Submit relevant IOCs to threat-intelligence systems
* Review filtering rules for financial-brand impersonation
* Provide phishing-awareness guidance to affected users
* Monitor for additional activity involving the identified infrastructure

---

## Full Report

[**View Full Investigation Report**](sample2.docx)

---

## Evidence

Supporting screenshots from the investigation are available in the `Screenshots/` directory.

```text
PHISH-002/
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
* Domain & Typosquatting Analysis
* URL Analysis
* IOC Extraction
* Social-Engineering Analysis
* Threat Analysis
* MITRE ATT&CK Mapping
* Security Recommendations
