# Practical Subnetting Breakdown  
### *A Human-Friendly Walkthrough for Real-World IT Work*

## 1. IP Address Classes (But Explained Like a Normal Person)

Every IPv4 address starts with a number that tells you what “class” it lives in. Think of classes as neighborhoods:

- **Class A** = huge neighborhoods  
- **Class B** = medium neighborhoods  
- **Class C** = small, tight-knit neighborhoods  

The only thing that matters? The **first octet**.

| Address        | First Octet | Neighborhood (Class) | Why |
|----------------|-------------|------------------------|-----|
| **192.168.1.1** | 192         | Class C                | 192–223 = Class C |
| **172.16.0.1**  | 172         | Class B                | 128–191 = Class B |
| **10.0.0.1**    | 10          | Class A                | 1–126 = Class A |

Simple. Clean. No drama.

---

## 2. Subnetting 192.168.10.0/24 — Borrowing Bits Like You're Taking PTO

We start with a /24 (255.255.255.0).  
That gives us 256 IP addresses but only **1 subnet**.  
Your company says: “We need more subnets.”  
Cool. Borrow **2 bits**.

### 2.a. How many subnets do we get?  
2² = **4 subnets**

### 2.b. How many hosts does each subnet hold?  
We borrowed 2 bits, so 6 host bits remain.  
2⁶ − 2 = **62 usable hosts** per subnet.

(Yes, we always subtract 2. Network + Broadcast are like the ‘lost socks’ of IP addressing since you never get to use them.)

### 2.c. What’s the subnet jump size?  
The new mask is /26 → 255.255.255.192  
Block size = 256 − 192 = **64**

So the subnets fall nicely like:

- 192.168.10.0  
- 192.168.10.64  
- 192.168.10.128  
- 192.168.10.192  

Each one a tidy little neighborhood of 62 hosts.

---

## 3. Designing 4 Subnets for 192.168.20.0/24  
Here’s where you pretend you’re the network architect for a mid-sized company and they need four cleanly separated subnets.

### 3.a. What mask do we need?
4 subnets → borrow 2 bits  
/24 + 2 = **/26**  
Mask = **255.255.255.192**

### 3.b. Break it down logically

Block size still: **64**  
Let’s map everything like a pro:

| Subnet | Network Address     | First Host          | Last Host           | Broadcast          |
|--------|----------------------|----------------------|----------------------|---------------------|
| 1      | 192.168.20.0         | 192.168.20.1         | 192.168.20.62        | 192.168.20.63       |
| 2      | 192.168.20.64        | 192.168.20.65        | 192.168.20.126       | 192.168.20.127      |
| 3      | 192.168.20.128       | 192.168.20.129       | 192.168.20.190       | 192.168.20.191      |
| 4      | 192.168.20.192       | 192.168.20.193       | 192.168.20.254       | 192.168.20.255      |

This is the kind of table network engineers sketch on whiteboards every day.

---

## 4. Troubleshooting a Real User Issue  
This is the part where someone calls the help desk and says:  
> “My Wi-Fi is broken.”  
But the IP tells the real story.

User’s info:  
- IP: **192.168.30.130**  
- Mask: **255.255.255.192 (/26)**

### 4.a. Is 192.168.30.130 even a valid host?  
Let’s break down the /26 ranges (increment of 64):

- 192.168.30.0 – 63  
- 192.168.30.64 – 127  
- **192.168.30.128 – 191** ← this is the one  
- 192.168.30.192 – 255  

The third subnet starts at 128, first host is 129, last is 190.

**130** is inside that range.  
So yes **the IP itself is valid.**

(Which means the problem isn’t the addressing, time to check gateway, DHCP, cable, Wi-Fi, etc.)

### 4.b. Correct subnet info for the user

| Item          | Value               |
|---------------|---------------------|
| Network       | 192.168.30.128      |
| First Host    | 192.168.30.129      |
| Last Host     | 192.168.30.190      |
| Broadcast     | 192.168.30.191      |

Now you have the exact boundary of the user’s subnet.

---

## Final Thoughts  
Subnetting isn’t about memorizing charts: it’s about recognizing patterns. Once you understand increments, borrowed bits, and how to find ranges, you can walk into any network, map it out, and look like the person who’s been doing this for years.
