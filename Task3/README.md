 🛡️ Task 3 — Basic Vulnerability Scan

Author: Yuvraj Yadav
Date: 27-10-2025
Platform Used: macOS (Nmap CLI Tool)
Target System: Localhost (IP: 127.0.0.1)
Scanner System: macOS (same machine)

---

 🎯 Objective

To perform a **basic vulnerability assessment** on a personal macOS system using the **Nmap vulnerability scanning engine**, identify open ports, detect running services, and evaluate potential risks based on CVSS scores.



⚙️ Tools Used

Nmap (v7.94)** — Open-source network scanner
macOS Terminal** — Command-line interface
Homebrew** — Used for installing Nmap

> Scan performed on localhost (`127.0.0.1`) to simulate internal vulnerability assessment.

---

📂 Repository Structure

Task-3_Basic_Vulnerability_Scan/
│
├── 📁 Reports/
│ ├── scan_basic.nmap
│ ├── scan_vuln.txt
│ └── report.md
│
├── 📁 Screenshots/
│ ├── 01_scan_start.png
│ ├── 02_port_scan.png
│ ├── 03_vuln_output.png
│ ├── 04_summary.png
│ └── 05_cvss_table.png
│
├── 📄 findings.csv
└── 📝 README.md



 🚀 Steps Performed

1. Installed **Nmap** using Homebrew:

   ```bash
   brew install nmap
   ```
2. Identified system IP address:

   ```bash
   ipconfig getifaddr en0
   ```
3. Executed **basic port and service scan**:

   ```bash
   sudo nmap -sS -sV -O 127.0.0.1 -oA scan_basic
   ```
4. Ran **vulnerability scan scripts**:

   ```bash
   sudo nmap --script vuln 127.0.0.1 -oN scan_vuln.txt
   ```
5. Collected results, identified key findings, and documented the report.
6. Verified mitigations and rescanned to ensure issues were resolved.

---
  Scan Summary

| **Parameter**               | **Details**                |
| --------------------------- | -------------------------- |
| Total Ports Scanned         | 1000                       |
| Open Ports Found            | 5                          |
| Detected Services           | SSH, HTTP, HTTPS, SMB, RPC |
| High-Risk Vulnerabilities   | 2                          |
| Medium-Risk Vulnerabilities | 1                          |
| Low/Informational           | 2                          |

Scan completed successfully with two high-risk vulnerabilities identified on local services.



 🧠 Key Findings

| Vulnerability**                 | **Severity** | **Description**                                       |
| --------------------------------- | ------------ | ----------------------------------------------------- |
| Outdated OpenSSH version detected | High         | Detected version allows potential brute-force attacks |
| SMBv1 protocol supported          | High         | Outdated protocol vulnerable to EternalBlue exploit   |
| TLS weak cipher suites enabled    | Medium       | Older TLS configurations detected                     |
| HTTP server banner disclosure     | Low          | Reveals server and version details                    |
| Host fingerprinting allowed       | Info         | OS and service details discoverable                   |

> **Result:** System contains a few outdated services that require updates and configuration hardening ⚠️

---

Mitigation Steps

Updated OpenSSH and disabled password login** for enhanced security.
Disabled SMBv1 protocol and enforced SMBv3 only.
Modified TLS configuration** to enforce TLSv1.2+.
Disabled HTTP server banner** disclosure. Applied
macOS security updates** and verified patch compliance.

 Re-ran Nmap — confirmed that vulnerabilities were mitigated.

---

## 📸 Screenshots

![Scan Start](Screenshots/01_scan_start.png)
![Port and Service Scan](Screenshots/02_port_scan.png)
![Vulnerability Output](Screenshots/03_vuln_output.png)
![Summary](Screenshots/04_summary.png)

---

 Outcome

 Successfully executed **vulnerability scanning** using Nmap on macOS.
 Understood how Nmap scripts (`--script vuln`) detect known CVEs.
 Learned to interpret scan results and prioritize vulnerabilities based on **CVSS**.
  Implemented mitigation and validation through re-scanning.



Key Learnings

Fundamentals of **host discovery**, **port scanning**, and **service detection**.
Exposure of outdated protocols and services (SSH, SMB, HTTP).
Importance of System Updates and Protocol Hardening.
Use of **CVSS scores** to rank and remediate issues effectively.

---

© 2025 Yuvraj Yadav — ElevateLabs Pvt. Ltd. Cyber Security Internship**



