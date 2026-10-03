# Healthcare-Web-Application-Penetration-testing

This repository contains the complete documentation, assessment methodology, vulnerability analysis, and proof-of-concept evidence for an authorized **Black-Box Web Application Penetration Testing Assessment** conducted against a target Healthcare Web Application (**Mediroza Patient Portal**).

---

## Executive Summary

As part of the **NETWORKWALKS Cybersecurity Internship (Batch B083 Int)**, an authorized black-box penetration testing assessment was performed to evaluate the overall security posture of a target healthcare web application. The assessment covered the complete security testing lifecycle—from initial reconnaissance and service enumeration through web application security testing, privilege escalation, protected document analysis, and remediation planning.

---

## 🔐 Authorization & Responsible Disclosure

This assessment was performed in an authorized educational environment with written permission from the program. The techniques documented here were used solely within the approved scope.

To protect the target organization and any sensitive information, this public repository contains **no unauthorized target identifiers, credentials, patient health information (PHI/PII), or unredacted internal server endpoints**.

---

## Project Objective

The objective of this assessment was to simulate a real-world external penetration test against a healthcare organization's public-facing web application.

The assessment focused on:
* External reconnaissance and service enumeration
* Web application attack-surface discovery
* Authentication and access-control testing
* Analysis of protected documents
* Security assessment of document encryption
* Investigation of evidence discovered during testing
* Identification of potential information-disclosure vulnerabilities
* Professional documentation and risk assessment

---

## Assessment Milestones

| Milestone | Objective |
| :--- | :--- |
| **M1 — Reconnaissance & Initial Access** | Enumerate external attack surface, identify application components, and evaluate authentication mechanisms. |
| **M2 — Protected File Analysis** | Analyze security mechanisms protecting retrieved documents and evaluate resistance to password recovery techniques. |
| **M3 — Follow-the-Evidence Investigation** | Investigate information discovered during prior testing to identify additional security exposures and attack chains. |
| **M4 — Security Reporting** | Consolidate findings into a formal penetration testing report with risk ratings, evidence, and remediation roadmaps. |

---

## 🛠️ Tools & Technologies Used

### Reconnaissance & Enumeration
* **Nmap** — Network scanning, service detection, and OS fingerprinting
* **Gobuster** — Web directory and endpoint brute-forcing
* **Nikto** — Web server misconfiguration and vulnerability scanning
* **WhatWeb** — Web technology fingerprinting and header analysis
* **WPScan** — WordPress CMS security assessment where applicable

### Web Application Testing
* **Burp Suite** — HTTP request interception, parameter analysis, and manual security testing

### Password & File Analysis
* **John the Ripper (Jumbo)** — Offline password hash cracking and evaluation
* **ExifTool** — Metadata extraction from document assets and images
* **pikepdf** — PDF structure and password encryption analysis
* **HexStrike-AI** — Automated vulnerability context aggregation

---

## ⚙️ Methodology & Execution Lifecycle

### 1. Reconnaissance
The assessment began with external reconnaissance to map the exposed attack surface. Automated scanner outputs were cross-validated using manual inspection and multi-tool verification to eliminate false positives caused by bot-protection or WAF challenges.

### 2. Web Application Assessment
Discovered web endpoints and authentication mechanisms were manually assessed using Burp Suite to evaluate session management, access control boundaries, and input handling.

### 3. Protected Document Assessment
Restricted patient lab reports were analyzed to determine password protection standards, structural characteristics, and encryption strengths without publicly exposing sensitive patient data.

### 4. Evidence-Based Investigation
Data uncovered during the document analysis phase was evaluated to uncover potential vulnerability chaining scenarios, illustrating how minor information leaks can expose broader attack surfaces.

---

## 🔍 High-Level Vulnerability Findings

### Finding 01 — Weak Authentication Surface
* **Impact:** Risk of unauthorized access, account compromise, and exposure of restricted functionality.
* **Recommendation:** Enforce unified authentication controls across all endpoints, implement strong password policies, multi-factor authentication (MFA), and rate-limiting.

### Finding 02 — Protected Document Security Weakness
* **Impact:** Susceptibility of encrypted document hashes to offline dictionary attacks, leading to potential confidential file exposure.
* **Recommendation:** Utilize strong, unique passphrases and modern encryption standards; enforce access control at the application layer rather than relying strictly on file-level encryption.

### Finding 03 — Metadata Information Disclosure
* **Impact:** Document metadata revealed internal paths, software versions, and system clues useful for secondary reconnaissance.
* **Recommendation:** Strip unnecessary metadata from public documents prior to publishing; establish automated file sanitization procedures.

### Finding 04 — Chained Information Exposure
* **Impact:** Multiple low-severity disclosures combined to form a high-impact exploit chain.
* **Recommendation:** Treat information disclosures as potential attack-chain drivers; enforce consistent authentication and perform periodic attack-surface reviews.

---

## 📷 Assessment Evidence & Proof of Concept

### Figure 1: Target Web Interface — Mediroza Patient Portal
Target patient portal interface displaying encrypted PDF lab report download endpoints (`S. Dlamini`, `P. Reddy`, `E. Thompson`).

![Target Web Interface](images/figure1.png)

### Figure 2: Password Hash Recovery — Test Key (123456)
Successful PDF hash derivation and dictionary recovery of key `123456`.

![Password Hash Recovery Test Key](images/figure2.png)

### Figure 3: Password Hash Recovery — Weak Key (password)
Successful extraction and match of weak default password `password`.

![Password Hash Recovery Weak Key](images/figure3.png)

### Figure 4: Password Hash Recovery — Special Character Key (!@#\$%^&*)
Wordlist traversal matching special character key string `!@#$%^&*`.

![Password Hash Recovery Special Key](images/figure4.png)

---

## 💡 Key Lessons Learned

1. **Reconnaissance is Only the Beginning:** Automated port scans provide initial surface visibility but do not replace deep, manual application testing.
2. **Validate Automated Scan Results:** Always cross-check tool findings to confirm actual exploitability and filter out proxy/WAF interference.
3. **Assess Protected Files Individually:** Never assume uniform security controls across all files; different documents may utilize distinct keys or algorithms.
4. **Metadata Matters:** Hidden metadata in documents can expose critical system, path, and user details.
5. **Small Vulnerabilities Chain Into Major Findings:** Minor information leaks often serve as the foundation for multi-stage exploit paths.

---

## Author & Program Context

* **Program:** Networkwalks Cybersecurity Internship Program
* **Batch:** Cybersecurity B083 Int
* **Instructor / Mentor:** Sir Waqas Karim (CCIE)
* **Focus Areas:** Web Application Security, Penetration Testing, Document Security, Vulnerability Assessment, Reporting

---

## ⚖️ Disclaimer

This repository is intended for educational and professional portfolio purposes only. The techniques and tools referenced here should only be executed against systems with explicit, written authorization. Unauthorized security testing is strictly illegal.
