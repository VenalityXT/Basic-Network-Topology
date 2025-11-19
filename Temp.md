# IP Addressing & Subnetting Walkthrough  
**On-the-Job Scenario: Network Expansion & Subnet Design**

This document provides a clear, step-by-step breakdown of the subnetting tasks, addressing calculations, and troubleshooting from the scenario. Use it as reference material to support your screenshots.

---

## 1. Understanding IP Address Classes

IP class is determined by the **first octet**:

- **Class A:** 1–126  
- **Class B:** 128–191  
- **Class C:** 192–223  

| IP Address     | First Octet | Class |
|----------------|-------------|--------|
| 192.168.1.1    | 192         | C      |
| 172.16.0.1     | 172         | B      |
| 10.0.0.1       | 10          | A      |

---

## 2. Subnetting 192.168.10.0/24 (Borrowing 2 Bits)

### 2.a. Number of Subnets  
Formula: 2^borrowed_bits  
- Borrowed bits: **2**  
- Subnets: **4**

### 2.b. Hosts per Subnet  
Host bits remaining: 32 − (24 + 2) = **6 bits**  
Formula: 2^host_bits − 2  
- Hosts = 2⁶ − 2 = **62 hosts per subnet**

### 2.c. Subnet Increment  
New prefix: /24 + 2 = **/26**  
Subnet mask: **255.255.255.192**  
Increment = 256 − 192 = **64**

Subnets:
- 192.168.10.0  
- 192.168.10.64  
- 192.168.10.128  
- 192.168.10.192  

---

## 3. Creating 4 Subnets from 192.168.20.0/24

### 3.a. New Subnet Mask  
Need 4 subnets → 2² = 4 → borrow **2 bits**  
- New prefix: **/26**  
- New mask: **255.255.255.192**

### 3.b. Subnet Table (/26)

Increment = 64

| Subnet | Network Address     | First Host          | Last Host           | Broadcast          |
|--------|----------------------|----------------------|----------------------|---------------------|
| 1      | 192.168.20.0         | 192.168.20.1         | 192.168.20.62        | 192.168.20.63       |
| 2      | 192.168.20.64        | 192.168.20.65        | 192.168.20.126       | 192.168.20.127      |
| 3      | 192.168.20.128       | 192.168.20.129       | 192.168.20.190       | 192.168.20.191      |
| 4      | 192.168.20.192       | 192.168.20.193       | 192.168.20.254       | 192.168.20.255      |

---

## 4. Troubleshooting Scenario

User IP: **192.168.30.130**  
Subnet mask: **255.255.255.192 (/26)**  

### 4.a. Is the IP Valid?  
/26 mask = increment of **64**

Subnets in this range:  
- 192.168.30.0 – 63  
- 192.168.30.64 – 127  
- **192.168.30.128 – 191** ← IP falls here  
- 192.168.30.192 – 255  

Range of the third subnet:
- **Network:** 192.168.30.128  
- **First host:** 192.168.30.129  
- **Last host:** 192.168.30.190  
- **Broadcast:** 192.168.30.191  

The given IP **192.168.30.130** is between 129 and 190 →  
✅ **Valid IP for this subnet**

### 4.b. Correct Subnet Range for This IP

| Item          | Value               |
|---------------|---------------------|
| Network       | 192.168.30.128      |
| First Host    | 192.168.30.129      |
| Last Host     | 192.168.30.190      |
| Broadcast     | 192.168.30.191      |

---

If you'd like, I can turn this into a GitHub-style README with badges and a description just like your other lab projects.  
