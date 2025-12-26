# Wireshark Network Analysis – ARP Traffic Investigation

## 📌 Project Overview
This project demonstrates a **basic network traffic analysis** using **Wireshark**, focusing on the inspection and interpretation of **ARP (Address Resolution Protocol)** traffic within a local network.

The goal of this analysis is to:
- Understand normal ARP behavior
- Identify broadcast traffic
- Differentiate between legitimate network activity and potential ARP-based attacks

This project reflects the type of packet-level analysis performed by **SOC Analysts** and **Network Security Analysts**.

---

## 🛠 Tools Used
- **Wireshark**
- Operating System: Windows
- Network Type: Local Area Network (LAN)

---

## 📡 Capture Details

### Packet Summary

***Frame Number: 10038
Timestamp: 681.533343 seconds
Source: Toxx xx_ad:xxx xxx:***
Destination: Broadcast
Protocol: ARP
Length: 42 bytes
Info: Who has 192.168.x.xx? Tell 192.1xx.x.x***


---

## 🔍 Step-by-Step Analysis

### 1️⃣ Identifying the Protocol
The packet was identified as **ARP (Address Resolution Protocol)**, which operates at **Layer 2 (Data Link Layer)** of the OSI model.

ARP is used to resolve:

# 🔗 IP Address → MAC Address

### 2️⃣ Source and Destination Analysis
- **Source MAC:** `TozxxKaxxxxi_xd:bxxxxx`
  - Vendor identification indicates a **network gateway or router**
- **Destination:** `Broadcast`
  - ARP requests are broadcast because the sender does not yet know the target MAC address

This behavior is expected and normal in LAN environments.

### 3️⃣ Message Interpretation

***Who has 192.1xx.0.xx? Tell 192.1xx.x.x***
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/58a2314e-7c2d-4b46-88eb-4c613918f3c4" />


This means:
- The device with IP **192.16x.x.1xx** (likely the router)
- Is requesting the MAC address of **192.16x.xx.1xx**
- The request is sent to all devices onq the network

If the device exists and is online, it will respond with its MAC address.

---

### 4️⃣ Packet Size Validation
- **Length:** 42 bytes  
This is the standard size for an ARP request, indicating no abnormal padding or manipulation.

---

## 🛡️ Security Assessment

### ✅ Normal Behavior Observed
The ARP request represents **legitimate network activity**, commonly caused by:
- ARP cache expiration
- A device reconnecting to the network
- Routine gateway checks
- DHCP lease renewals

---

### ⚠️ Potential ARP Threats (Not Observed)
This capture **did NOT** show indicators of:
- ARP poisoning
- ARP spoofing
- Man-in-the-middle attacks
- ARP flooding or storms

Indicators of malicious ARP behavior would include:
- Multiple IPs resolving to the same MAC
- Unsolicited ARP replies
- Excessive ARP traffic in short time intervals

---

## 📊 Outcome & Conclusion

- The ARP packet analyzed was **benign and expected**
- No suspicious or malicious activity was detected
- The traffic aligns with normal LAN address resolution behavior
- This analysis establishes a **baseline understanding of ARP traffic**, which is critical for identifying future anomalies

---

## 🧠 Skills Demonstrated
- Packet capture and inspection
- ARP protocol analysis
- Layer 2 networking concepts
- Network baseline identification
- Security-focused traffic interpretation
- Wireshark filtering and analysis

---

## 🚀 Next Steps
Planned extensions of this project include:
- Simulating ARP spoofing in a controlled lab environment
- Comparing normal ARP traffic vs malicious ARP behavior
- Importing PCAP files into **Splunk** for log correlation
- Creating SOC-style alerts and dashboards

---





