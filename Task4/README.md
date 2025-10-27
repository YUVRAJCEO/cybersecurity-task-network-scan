
Task 4 — Setup and Use a Firewall on macOS (UFW)

**Author:** Yuvraj Yadav  
**Date:** 28-10-2025  
**Platform Used:** macOS (Intel-based)  
**Firewall Tool:** Uncomplicated Firewall (UFW via Homebrew CLI)  

---

## 🎯 Objective
To configure and test basic firewall rules on macOS using **UFW (Uncomplicated Firewall)**.  
The aim is to **block insecure traffic (Telnet port 23)**, **allow trusted services (SSH port 22)**, and understand how firewall rules filter inbound and outbound network connections.

---

## ⚙️ Tools Used
- **macOS Terminal**
- **UFW (v0.36+)**
- **Homebrew** (for installation)
- **Netcat (nc)** (for port testing)

---

## 📂 Repository Structure
```

Task-4_Firewall_Configuration/
│
├── 📁 Screenshots/
│   ├── 01_ufw_status.png
│   ├── 02_ufw_enable.png
│   ├── 03_ufw_rules.png
│   ├── 04_telnet_block.png
│   └── 05_ssh_allow.png
│
├── 📝 README.md
├── 📄 report.md
└── 📄 firewall_rules.txt

````

---

## 🚀 Steps Performed

1. **Installed UFW**  
   ```bash
   brew install ufw
````

2. **Checked initial status**

   ```bash
   sudo ufw status
   ```

3. **Enabled UFW and set default policies**

   ```bash
   sudo ufw default deny incoming
   sudo ufw default allow outgoing
   sudo ufw enable
   ```

4. **Blocked Telnet (port 23)**

   ```bash
   sudo ufw deny 23
   ```

5. **Allowed SSH (port 22)**

   ```bash
   sudo ufw allow 22
   ```

6. **Verified rules**

   ```bash
   sudo ufw status numbered
   ```

7. **Tested rules using Netcat**

   ```bash
   nc -zv 127.0.0.1 23   # should fail
   nc -zv 127.0.0.1 22   # should succeed
   ```

8. **Reset rules after testing**

   ```bash
   sudo ufw reset
   ```

---

🧩 Firewall Rules Summary

| Rule ID | Action | Port / Service | Protocol | Purpose                | Status |
| :-----: | :----- | :------------- | :------- | :--------------------- | :----- |
|    1    | DENY   | 23             | TCP      | Block Telnet traffic   | Active |
|    2    | ALLOW  | 22             | TCP      | Permit SSH connections | Active |

---

Key Learnings

* Firewalls enforce **traffic filtering** through inbound/outbound rules.
* **UFW** simplifies firewall configuration with human-readable syntax.
* Blocking **unused ports** like Telnet reduces attack surface.
* Proper **testing** ensures valid rule behavior before deployment.
* Understanding **stateful vs stateless** inspection improves network security design.

---

Screenshots Included

* `01_ufw_status.png` – Initial state
* `02_ufw_enable.png` – Firewall activation
* `03_ufw_rules.png` – Applied rules
* `04_telnet_block.png` – Port 23 blocked
* `05_ssh_allow.png` – Port 22 allowed

---

Outcome

Successfully configured and tested firewall rules on macOS using UFW.
Traffic on Telnet (port 23) was blocked, while SSH (port 22) remained accessible.
This demonstrated practical skills in firewall setup, traffic control, and rule verification.



© 2025 Yuvraj Yadav — ElevateLabs Pvt. Ltd. Cyber Security Internship**

```

---


