# 🔐 Standard Access Control List (ACL) – Cisco Lab

## 📌 Project Overview

This project demonstrates the configuration and implementation of a **Standard Access Control List (ACL)** on a Cisco Router.

The ACL is configured to:
- ✅ Permit only specific hosts from the IT department
- ❌ Deny all other traffic
- 🎯 Apply filtering on inbound traffic

This lab was implemented using Cisco Packet Tracer.

---

## 🧠 What is a Standard ACL?

A **Standard Access Control List** filters traffic based only on the **source IP address**.

- Uses ACL numbers: **1–99**
- Does NOT filter by destination IP or port
- Best practice: Place it **close to the destination**

---

## 🏗️ Network Topology

- IT Department: `192.168.1.0/24`
- Server Network: `10.10.10.0/24`
- Router connects both networks
- ACL applied inbound on `GigabitEthernet0/0`

📎 See topology diagram inside `/docs/topology.png`

---

## 🎯 ACL Objective

Allow only:
- `192.168.1.10`
- `192.168.1.20`

Deny all other hosts from accessing the network.

---

## ⚙️ Router Configuration

```bash
enable
configure terminal

access-list 10 permit host 192.168.1.10
access-list 10 permit host 192.168.1.20
access-list 10 deny any

interface gig0/0
ip access-group 10 in
exit

write memory
```

---

## 🔎 Verification Commands

```bash
show access-lists
show ip interface gig0/0
```

---

## 🧹 How to Remove the ACL

```bash
no access-list 10
```

If applied on interface:

```bash
interface gig0/0
no ip access-group 10 in
```

---

## 📚 Key Learning Outcomes

- Understanding Standard ACL logic
- Source-based traffic filtering
- Interface-based ACL application
- Verification and removal process

---

## 👨‍💻 Author

Ankit Kuttarmare  
Master’s in Computer Science  
Networking & Security Projects
