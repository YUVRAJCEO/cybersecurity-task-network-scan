
 🛡️ Task 4 — Setup and Use a Firewall on Linux (UFW)

**Author:** Yuvraj Yadav  
**Date:** 28-10-2025  
**Platform Used:** Ubuntu 22.04 LTS / Kali Linux  
**Firewall Tool:** Uncomplicated Firewall (UFW)  

---

 🎯 Objective
To configure and test basic firewall rules on **Linux** using **UFW (Uncomplicated Firewall)**.  
The goal is to **block insecure ports (Telnet – 23)**, **allow trusted services (SSH – 22)**, and understand how a firewall filters network traffic based on inbound and outbound policies.

---

 ⚙️ Tools Used
- **Operating System:** Ubuntu / Kali Linux  
- **Firewall Tool:** UFW (v0.36 or higher)  
- **Testing Tool:** Netcat (`nc`)  
- **Terminal:** Bash / Z Shell  

---

📂 Repository Structure
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

 🚀 Steps Performed

1. **Install UFW**
   ```bash
   sudo apt update
   sudo apt install ufw -y
````

2. **Check UFW Status**

   ```bash
   sudo ufw status
   ```

   *Expected Output:* `Status: inactive`

3. **Enable UFW and Set Default Policies**

   ```bash
   sudo ufw default deny incoming
   sudo ufw default allow outgoing
   sudo ufw enable
   ```

   *Result:* Firewall enabled and persistent on boot.

4. **Block Telnet (Port 23)**

   ```bash
   sudo ufw deny 23
   ```

5. **Allow SSH (Port 22)**

   ```bash
   sudo ufw allow 22
   ```

6. **Verify Rules**

   ```bash
   sudo ufw status numbered
   ```

7. **Test Ports with Netcat**

   ```bash
   nc -zv 127.0.0.1 23   # should fail (blocked)
   nc -zv 127.0.0.1 22   # should succeed (allowed)
   ```

8. **Reset Firewall (After Testing)**

   ```bash
   sudo ufw reset
   ```

   *Result:* All rules cleared and defaults restored.

---

## 🧩 Firewall Rules Summary

| Rule ID | Action | Port / Service | Protocol | Purpose                         | Status |
| :-----: | :----- | :------------- | :------- | :------------------------------ | :----- |
|    1    | DENY   | 23             | TCP      | Block Telnet (insecure)         | Active |
|    2    | ALLOW  | 22             | TCP      | Allow SSH (secure remote login) | Active |

---

## 🧠 Key Learnings

* Firewalls filter traffic based on defined rules to protect systems.
* **UFW** simplifies `iptables` management with easy commands.
* Blocking unused ports (e.g., Telnet, FTP) reduces attack surface.
* Default policies (deny incoming, allow outgoing) provide a secure baseline.
* Understanding **stateful packet inspection** helps manage connections safely.

---

## 📸 Screenshots Included

* `01_ufw_status.png` – Initial UFW status
* `02_ufw_enable.png` – Firewall activation
* `03_ufw_rules.png` – Applied rules list
* `04_telnet_block.png` – Port 23 blocked (test failed)
* `05_ssh_allow.png` – Port 22 allowed (test successful)

---

## 🧾 Outcome

Successfully configured and tested UFW firewall rules on Linux.
Blocked Telnet (23) and allowed SSH (22), confirming correct traffic filtering.
Gained practical experience in Linux firewall setup, testing, and security best practices.

---

**© 2025 Yuvraj Yadav — ElevateLabs Pvt. Ltd. Cyber Security Internship**



