
🧭 Task 5 — Capture and Analyze Network Traffic Using Wireshark  

**Author:** Yuvraj Yadav  
**Date:** 29-10-2025  
**Platform Used:** macOS  
**Tool Used:** Wireshark (v4.x)  

---

🎯 Objective
To capture live network traffic using **Wireshark**, analyze packets exchanged over common network protocols, and identify how communication occurs at different layers of the **TCP/IP** stack.  
The task demonstrates packet capture, protocol filtering, and basic network forensics skills.

---

⚙️ Tools Used
- **Wireshark** (v4.x) — GUI network analyzer  
- **macOS Wi-Fi Adapter (en0)** — active network interface  
- **Ping Utility** and **Web Browser** — to generate traffic  

---

📂 Repository Structure
```

Task-5_Network_Traffic_Analysis/
│
├── 📁 Screenshots/
│   ├── 01_start_capture.png
│   ├── 02_dns_filter.png
│   ├── 03_http_traffic.png
│   ├── 04_tls_handshake.png
│   └── 05_icmp_ping.png
│
├── 📝 README.md
├── 📄 report.md
└── 📁 network_capture_yuvraj.pcapng

````

---

 🚀 Steps Performed

1. Installed Wireshark**  
   ```bash
   brew install wireshark
````

2. **Started Capture**

   * Opened Wireshark → Selected Wi-Fi (en0) → Clicked Start Capture
   * Browsed websites and pinged servers to generate traffic

3. **Stopped Capture** after ≈1 minute and saved as `network_capture_yuvraj.pcapng`

4. **Applied Display Filters** to study protocols:

   * DNS → `dns`
   * HTTP → `http`
   * HTTPS → `tls`
   * ICMP → `icmp`
   * ARP → `arp`

5. **Analyzed Packets** for each protocol (header details, ports, and communication patterns)

6. **Exported and Documented** findings with screenshots and report.

---

## Protocols Identified

| Protocol | Layer       | Port | Description                                    |
| :------- | :---------- | :--: | :--------------------------------------------- |
| DNS      | Application |  53  | Domain name resolution queries & responses     |
| HTTP     | Application |  80  | Unencrypted web traffic (GET/POST requests)    |
| HTTPS    | Application |  443 | Encrypted web traffic with TLS handshake       |
| ICMP     | Network     |   —  | Ping requests/replies for connectivity testing |
| ARP      | Data Link   |   —  | Resolves IP to MAC addresses on local network  |

---

🧠 Key Learnings

* How Wireshark captures and decodes packets in real time.
* Practical use of filters to focus on specific protocols.
* Difference between **HTTP** (plaintext) and **HTTPS** (encrypted).
* Role of DNS and ARP in normal network operations.
* Importance of packet capture in **troubleshooting** and **cyber forensics**.

---

 📸 Screenshots Included

* `01_start_capture.png` – Wireshark interface during capture
* `02_dns_filter.png` – DNS queries and responses
* `03_http_traffic.png` – HTTP requests shown in plaintext
* `04_tls_handshake.png` – Encrypted HTTPS session initiation
* `05_icmp_ping.png` – ICMP echo request and reply packets

---

🧾 Outcome

Successfully captured and analyzed live network traffic using Wireshark on macOS.
Identified five distinct protocols (DNS, HTTP, HTTPS, ICMP, ARP) and understood their roles within the TCP/IP stack.
Enhanced practical skills in packet analysis, protocol filtering, and network diagnostics.

---

© 2025 Yuvraj Yadav — ElevateLabs Pvt. Ltd. Cyber Security Internship**

```

---

This README** matches the exact internship requirements for Task 5:  
- Packet capture ✔️  
- At least 3 protocols identified ✔️  
- Filtering and analysis explained ✔️  
- `.pcapng` file referenced ✔️  
- Screenshots and report linked ✔️  

