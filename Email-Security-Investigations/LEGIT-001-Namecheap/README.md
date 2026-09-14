# LEGIT-001 — Namecheap Domain Renewal Email Analysis

## Overview

This project documents the analysis of an email claiming to be a **Namecheap domain renewal notice**.

Unlike the phishing investigations in PHISH-001 and PHISH-002, this investigation resulted in a **benign assessment** after examining the email's headers, authentication results, sender infrastructure, domains, URLs, and overall message characteristics.

**Verdict:** Benign — Legitimate Domain Renewal Email
**Confidence:** High
**Sample ID:** LEGIT-001

---

## Objective

The objective of this investigation was to determine whether the email was a legitimate Namecheap communication or a potential phishing attempt by analyzing:

* Email metadata and headers
* Sender and recipient information
* SPF, DKIM, and DMARC results
* Sending infrastructure
* Sender and Reply-To domains
* Embedded URLs
* Domain relationships
* Email content and branding
* Indicators that could distinguish legitimate communication from phishing

---

## Investigation Methodology

The investigation followed a structured email-analysis process:

1. **Email Metadata Analysis**

   * Reviewed the sender, recipient, subject, timestamps, Reply-To, and Return-Path information.

2. **Header Analysis**

   * Examined SPF, DKIM, and DMARC authentication results.
   * Reviewed the Received chain to understand the email's delivery path.
   * Compared the observed infrastructure with the claimed sender identity.

3. **Domain & Infrastructure Analysis**

   * Examined the sender domains and related infrastructure.
   * Evaluated whether the observed domains and services were consistent with Namecheap's legitimate email ecosystem.

4. **URL Analysis**

   * Examined the links contained in the message.
   * Evaluated the destination domains and URL structure.
   * Considered whether the links were consistent with the claimed service.

5. **Content Analysis**

   * Reviewed the email's branding, domain-renewal context, and message structure.
   * Looked for common phishing indicators such as suspicious requests, deceptive domains, or unusual formatting.

6. **Verdict Assessment**

   * Combined authentication, infrastructure, URL, domain, and content findings to determine whether the message was legitimate.

---

## Key Findings

### Authentication Results

The email produced authentication results consistent with legitimate sending infrastructure.

The investigation examined **SPF, DKIM, and DMARC** and found alignment supporting the legitimacy of the message.

### Sender Infrastructure

The observed sending infrastructure was consistent with the expected infrastructure associated with the email and did not reveal an obvious impersonation or unauthorized sender.

### Domain Analysis

The domains associated with the email were consistent with the Namecheap domain-renewal context examined during the investigation.

No significant domain-impersonation indicator was identified.

### URL Analysis

The embedded URLs were examined as part of the investigation.

The destinations and URL characteristics did not provide sufficient evidence to classify the email as malicious.

### Overall Assessment

The combined technical and contextual evidence supported a legitimate interpretation of the message rather than a phishing attempt.

---

## Indicators Reviewed

| Indicator              | Analysis                                                 |
| ---------------------- | -------------------------------------------------------- |
| Sender Domain          | Consistent with the investigated Namecheap communication |
| SPF                    | Authentication result supported legitimacy               |
| DKIM                   | Authentication result supported message integrity        |
| DMARC                  | Authentication/alignment supported legitimacy            |
| Sending Infrastructure | Consistent with the investigated sender                  |
| URLs                   | No significant malicious indicator identified            |
| Email Content          | Consistent with the domain-renewal context               |

---

## Verdict

**Benign — Legitimate Domain Renewal Email**

**Confidence: High**

The email was assessed as legitimate based on the combined analysis of:

* SPF authentication
* DKIM authentication
* DMARC alignment
* Sender infrastructure
* Domain relationships
* URL analysis
* Email content and context

The investigation demonstrates the importance of evaluating multiple technical indicators rather than classifying an email based solely on its appearance.

---

## Recommended Actions

As the email was assessed as legitimate, no malicious-email containment action was required.

The analysis can instead serve as a **legitimate-email baseline** for comparison with suspicious messages.

Comparing legitimate and malicious emails can help identify differences in:

* Authentication
* Sender infrastructure
* Domain relationships
* URL destinations
* Message characteristics

---

## Full Report

[**View Full Investigation Report**](./Report.docx)

---

## Evidence

Supporting screenshots from the analysis are available in the `Screenshots/` directory.

```text id="q2p7sk"
LEGIT-001/
├── README.md
├── Report.docx
└── Screenshots/
```

---

## Skills Demonstrated

* Email Header Analysis
* SPF / DKIM / DMARC Analysis
* Email Infrastructure Analysis
* Domain Analysis
* URL Analysis
* Legitimate Email Verification
* Phishing Detection & Comparison
* Evidence-Based Assessment
* Security Analysis
