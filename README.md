# Cisco Packet Tracer Project – Advanced Networking with VLSM, DHCP, ACLs, Routing, and Redistribution

## 🔧 Project Overview

This project demonstrates an advanced network design and implementation using **Cisco Packet Tracer**. The network is built by applying **VLSM (Variable Length Subnet Masking)** based on specific host requirements, which are derived and planned using the [Davidc.net VLSM Calculator](https://www.davidc.net/sites/default/vlsmcalc.htm).

The project includes:
- VLSM-based IP addressing
- Inter-network connectivity
- DHCP configuration
- Access Control Lists (ACLs)
- Email Server setup
- Multi-protocol routing: RIP, OSPF (multi-area), and EIGRP
- Route redistribution across different protocols

---

## 🗺️ Network Planning

The IP scheme was developed using VLSM to efficiently allocate addresses to various subnets with specific host requirements. Refer to the images in the `/planning` directory for the detailed breakdown. Each network (A to K) was assigned its own subnet based on host requirements, with leftover addresses conserved.

---

## ✅ Key Features

### 📐 VLSM Implementation
- Used the VLSM calculator from [davidc.net](https://www.davidc.net/sites/default/vlsmcalc.htm).
- Allocated IPs to networks A–K based on exact host counts.
- Ensured minimal IP wastage and scalable addressing.
  
📷 **Host Requirements screenshot below:**

![Requirements Table](images/host_requirement.png)]]

📷 **SubNets screenshot below:**

![Subnets Table](images/VLSM.png)]]

---

### 🌐 Network-to-Network Connectivity
- All networks are interconnected via routers.
- Point-to-point links are assigned /30 or other small subnets to conserve IP space.

---

### 🖧 DHCP Configuration
- Configured DHCP on routers to dynamically assign IPs to end devices in each subnet.
- Reserved static IPs for gateways and servers.
- DHCP pools reflect the VLSM-planned subnets.

📷 **DHCP configuration screenshot below:**

![DHCP Configuration](images/DHCP_CONFIG.png)

---

### 🔐 Access Control Lists (ACLs)
- An **ACL** is used to block **Network J** from accessing **Network K**.
- All other networks retain normal access to K.
- ACLs are applied in the inbound/outbound direction depending on topology layout.

📷 **ACL screenshot below:**

![ACL Configuration](images/ACL_CONFIG.png)

---

### 📧 Email Server (Network K)
- Deployed an email server inside **Network K**.
- Configured SMTP and POP3 services.
- Clients from other networks (except Network J) can send/receive emails.

📷 **Email Server screenshot below:**

![Email Server Configuration](images/EMAIL_CONFIG.png)

---

### 🛰️ Routing Protocols
- Used a combination of routing protocols across network areas:
  - **RIP** for simpler legacy segments.
  - **OSPF** (Area 1 and Area 2) for organized, scalable routing.
  - **EIGRP** for performance-focused regions.
  
- Proper `network` statements and area assignments are done per protocol.

---

### 🔁 Route Redistribution
- Redistribution implemented between different routing protocol boundaries:
  - **RIP ↔ OSPF**
  - **OSPF ↔ EIGRP**
  
- Route redistribution ensures end-to-end connectivity across different domains.
- `default-information originate`, route-maps, and metric adjustments are used as needed.

---

## 🛠️ Technologies Used

- **Cisco Packet Tracer**
- **Routing Protocols**: RIP, OSPF (Area 1 and 2), EIGRP
- **Services**: DHCP, ACLs, SMTP/POP3 (Email)
- **Planning Tool**: [Davidc.net VLSM Calculator](https://www.davidc.net/sites/default/vlsmcalc.htm)

---

## 📂 Files Included

- `project.pkt`: Cisco Packet Tracer topology file
- `README.md`: This documentation
- `images/`: Folder containing configuration screenshots

---

## 🚦 Testing & Verification

- ✅ Successful ping between all permitted networks
- ✅ DHCP leases confirmed via `ipconfig /all` on PCs
- ✅ Email communication verified between networks (except J→K)
- ✅ ACL hit counters validated using `show access-lists`
- ✅ Routing tables and redistributions checked using `show ip route`

---

## 📌 Notes

- IP addressing is tightly optimized using VLSM
- Redistributed routes include proper metric handling
- Project topology supports future expansion and real-world deployment concepts

---

