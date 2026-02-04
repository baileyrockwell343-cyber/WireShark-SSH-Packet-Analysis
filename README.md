# Wireshark Packet Analyzer – SSH 

**Author:** Bailey Rockwell  
**Project Type:** Network Traffic Analysis (Wireshark + PuTTY)  
**Focus:** Secure remote access traffic validation + plaintext vs encrypted comparison

This repository documents a packet-capture lab using **Wireshark** to observe and explain an **SSH session (TCP/22)** between a Windows host and an Ubuntu host, including a short security comparison against **Telnet (TCP/23)**. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

---

## 📌 Project Overview

This lab uses two VMs/hosts:

- **Ubuntu machine:** `192.168.50.100` 
- **Windows 10 machine:** `192.168.50.50` 

The workflow is:
1. Configure static IPs on both hosts 
2. Verify connectivity with ping (both directions) 
3. Use **PuTTY** on Windows to SSH into Ubuntu over **port 22** 
4. Validate login + identity with `whoami` 
5. Observe and describe SSH traffic in Wireshark (SYN → SYN/ACK → ACK, then encrypted SSHv2) 

---

## 🎯 Objectives

- Confirm host-to-host communication using ICMP (ping)
- Generate a real SSH session using PuTTY (Windows → Ubuntu)
- Capture and interpret the traffic in Wireshark
- Explain why SSH traffic is encrypted and why Telnet traffic would expose credentials in plaintext 

---

## 🧪 Lab Environment

**Provisioning**
- Ubuntu machine + Windows 10 machine 

**Tools**
- Wireshark (packet capture + filtering)
- PuTTY (SSH client)
- Ubuntu terminal utilities (`ping`, `whoami`)

---

## 🧩 Network Configuration

### Ubuntu (Static IP)
Set the Ubuntu adapter IP to:
- `192.168.50.100` :contentReference[oaicite:13]{index=13}  

### Windows (Static IP)
Set the Windows adapter IP to:
- `192.168.50.50` :contentReference[oaicite:14]{index=14}  

### Connectivity Verification
- Ping Ubuntu host to confirm reachability :contentReference[oaicite:15]{index=15}  
- Ping Windows host to confirm reachability :contentReference[oaicite:16]{index=16}  

---

## 🚀 Procedure

### 1) Start Wireshark capture (Windows)
- Select the active interface
- Start capture
- filter SSH traffic:  
  - `ip.addr == 192.168.50.100 || ip.addr == 192.168.50.50`

### 2) SSH from Windows → Ubuntu using PuTTY
On the Windows host in **PuTTY**:
- Host/IP: `192.168.50.100` :contentReference[oaicite:17]{index=17}  
- Port: `22` (SSH) :contentReference[oaicite:18]{index=18}  
- Connection type: SSH :contentReference[oaicite:19]{index=19}  

Login and verify identity:
```bash
whoami
