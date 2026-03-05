# Windows Network Troubleshooting Lab — DNS Failure Simulation

## 📌 Overview

This lab simulates a real-world Help Desk troubleshooting scenario involving DNS misconfiguration on a Windows 10 client machine. The objective was to diagnose and resolve an issue where internet connectivity appeared functional, but websites could not be accessed.

The lab was performed in a virtualized environment to safely practice troubleshooting methodologies used in IT Support and Service Desk roles.

---

## 🎯 Objectives

- Practice structured troubleshooting methodology
- Understand DNS functionality within TCP/IP networking
- Diagnose connectivity vs name resolution issues
- Use common Windows networking tools
- Document incident resolution like a real support ticket

---

## 🖥️ Lab Environment

| Component | Configuration |
|---|---|
| Platform | Virtual Machine |
| OS | Windows 10 |
| Network Mode | NAT |
| Tools Used | Command Prompt, Network Adapter Settings |
| Commands | ipconfig, ping, nslookup |

---

## Scenario

A user reports:

> "My internet is connected, but websites will not load."

Initial testing confirmed network connectivity existed, indicating a likely DNS resolution issue.

---

## 1️⃣ — Baseline Verification

Verified normal network operation before introducing failure.

### Actions:
- Checked IP configuration
- Verified gateway and DNS assignment
- Confirmed internet connectivity

Commands used:

ipconfig /all
![ipconfig/all](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/ipconfigbaseline.png)

ping 8.8.8.8
![Ping 8.8.8.8](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/pingipsuccess.png)

nslookup google.com
![nslookup](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/nslookupsuccess.png)

✅ Result: Network functioning normally.

---

## 2️⃣ — Simulating the Issue

DNS settings were manually modified to invalid DNS servers to simulate a misconfiguration.

### Change Made:

Preferred DNS: 192.168.200.200

Alternate DNS: 192.168.200.201

![Manual Configuration](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/dnsmanualconfig.png)

---

## 3️⃣ — Issue Observation

Testing revealed:

| Test | Result |
|---|---|
| ping 8.8.8.8 | ✅ Success |
| ping google.com | ❌ Failed |

This confirmed:
- Network connectivity was working
- DNS resolution was failing

![Issue Observation](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/dnsfailurepingdomain.png)

---

## 4️⃣ — Troubleshooting Process

### 1. Confirm Symptoms
ping google.com

![Symptom Confirmation](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/confirmdnsfailure.png)

### 2. Inspect Network Configuration
ipconfig /all

Identified incorrect DNS server entries.

![Network Configuration](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/baddnsserver.png)

### 3. Attempt Standard Fix
ipconfig /flushdns

Issue persisted, indicating configuration-level problem.

![Standard Fix](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/flushdns.png)

---

## 5️⃣ — Resolution

Corrected DNS configuration:

- Set DNS to **Obtain automatically**
- Renewed network configuration

Commands used:

ipconfig /release

ipconfig /renew

![Resolution](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/iprenew.png)

---

## 6️⃣ — Verification

Connectivity restored successfully.

ping google.com

✅ DNS resolution working normally.

![Verification](https://github.com/granthuber/Windows-Network-Troubleshooting-Lab/blob/2569fb5b96924f44276e54b10c806736f8c502a0/dnsrestored.png)

---

##  Key Concepts Demonstrated

- DNS (Domain Name System)
- TCP/IP troubleshooting workflow
- Connectivity vs resolution testing
- Root cause analysis
- Incident documentation
- Tier 1 escalation methodology

---

##  What I Learned

This lab reinforced the importance of structured troubleshooting by isolating network layers. Testing connectivity by IP address before domain name resolution helped quickly identify DNS as the root cause.

I also practiced documenting troubleshooting steps clearly, similar to real Help Desk ticket workflows.

---

##  Skills Practiced

- Windows Networking
- DNS Troubleshooting
- Command Line Networking Tools
- Problem Isolation
- Technical Documentation
