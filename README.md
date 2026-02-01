# -Packet-Tracer-Lab-Implement-Basic-Connectivity-Basic-Switch-Configuration-
This lab focuses on basic Layer 2 switch configuration and network connectivity using Cisco Packet Tracer. The goal is to configure switch management interfaces (SVIs), assign IP addresses to end devices, and verify connectivity using common IOS show and ping commands.

# 🧪 Packet Tracer Lab: Implement Basic Connectivity (Basic Switch Configuration)

## 📌 Lab Overview
This lab focuses on **basic Layer 2 switch configuration and network connectivity** using Cisco Packet Tracer. The goal is to configure switch management interfaces (SVIs), assign IP addresses to end devices, and verify connectivity using common IOS **show** and **ping** commands.

## 🎯 Objectives
- Perform basic configuration on Cisco switches (S1 and S2)
- Configure switch management interfaces using **SVI (VLAN 1)**
- Assign IP addresses to PCs
- Verify end-to-end network connectivity

## 🗺️ Network Addressing Table

| Device | Interface | IP Address       | Subnet Mask       |
|--------|-----------|----------------|-----------------|
| S1     | VLAN 1    | 192.168.1.253  | 255.255.255.0   |
| S2     | VLAN 1    | 192.168.1.254  | 255.255.255.0   |
| PC1    | NIC       | 192.168.1.1    | 255.255.255.0   |
| PC2    | NIC       | 192.168.1.2    | 255.255.255.0   |

## 🧱 Lab Topology Assumptions
- All devices are connected within the same LAN
- Default VLAN (VLAN 1) is used for switch management
- No routing is required (single subnet)
- Connectivity is verified using ICMP (ping)

## ⚙️ Configuration and Verification

Click each device and perform the following:

### S1 Configuration
1. Enter privileged EXEC and global configuration mode:
enable
configure terminal
Set hostname:

hostname S1
Configure VLAN 1 interface for management:


interface vlan 1
 ip address 192.168.1.253 255.255.255.0
 no shutdown
end
copy running-config startup-config
Verify IP configuration:


show ip interface brief
Expected output:


Vlan1  192.168.1.253  YES manual  up  up
S2 Configuration
Enter global configuration mode and set hostname:


enable
configure terminal
hostname S2
Configure VLAN 1 interface for management:


interface vlan 1
 ip address 192.168.1.254 255.255.255.0
 no shutdown
end
copy running-config startup-config
Verify IP configuration:


show ip interface brief
Expected output:


Vlan1  192.168.1.254  YES manual  up  up
PC Configuration
Configure PC1 IP settings:

IP Address: 192.168.1.1

Subnet Mask: 255.255.255.0

Configure PC2 IP settings:

IP Address: 192.168.1.2

Subnet Mask: 255.255.255.0
(Configured via Desktop → IP Configuration in Packet Tracer)

Connectivity Verification
From PC1 Command Prompt:


ping 192.168.1.253
ping 192.168.1.254
ping 192.168.1.2
From PC2 Command Prompt:


ping 192.168.1.254
ping 192.168.1.253
ping 192.168.1.1
✅ All pings should be successful (initial 80% success may occur due to ARP resolution).

From S1:


ping 192.168.1.1
ping 192.168.1.2
ping 192.168.1.254
From S2:


ping 192.168.1.1
ping 192.168.1.2
ping 192.168.1.253
Expected result:

Success rate is 100 percent (5/5)
✅ Key Concepts Practiced
Switch hostname configuration

Switch Virtual Interface (SVI)

Layer 2 switching vs Layer 3 management

IP addressing in a flat network

Connectivity verification using ping

IOS verification commands (show ip interface brief)

📚 Tools Used
Cisco Packet Tracer

Cisco IOS CLI

🧠 Lessons Learned
A switch does not need an IP address to forward traffic, but it does need one for management

SVIs provide Layer 3 access to Layer 2 switches

Proper verification is as important as configuration
