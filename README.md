# -Packet-Tracer-Lab-Implement-Basic-Connectivity-Basic-Switch-Configuration-
This lab focuses on basic Layer 2 switch configuration and network connectivity using Cisco Packet Tracer. The goal is to configure switch management interfaces (SVIs), assign IP addresses to end devices, and verify connectivity using common IOS show and ping commands.

🎯 Objectives

Perform basic configuration on Cisco switches (S1 and S2)

Configure switch management interfaces using SVI (VLAN 1)

Assign IP addresses to PCs

Verify end-to-end network connectivity

🗺️ Network Addressing Table
Device	Interface	IP Address	Subnet Mask
S1	VLAN 1	192.168.1.253	255.255.255.0
S2	VLAN 1	192.168.1.254	255.255.255.0
PC1	NIC	192.168.1.1	255.255.255.0
PC2	NIC	192.168.1.2	255.255.255.0
🧱 Lab Topology Assumptions

All devices are connected within the same LAN

Default VLAN (VLAN 1) is used for switch management

No routing is required (single subnet)

Connectivity is verified using ICMP (ping)

⚙️ Configuration Steps
🔹 Part 1: Basic Switch Configuration (S1 & S2)
Step 1: Configure Hostnames
enable
configure terminal
hostname S1


(Repeat for S2 using hostname S2)

Step 2: Configure Switch Management Interface (SVI)

S1 Configuration

interface vlan 1
 ip address 192.168.1.253 255.255.255.0
 no shutdown
end
copy running-config startup-config


Verification

show ip interface brief


Expected output:

Vlan1  192.168.1.253  YES manual  up  up


S2 Configuration

interface vlan 1
 ip address 192.168.1.254 255.255.255.0
 no shutdown
end
copy running-config startup-config


Verification

show ip interface brief


Expected output:

Vlan1  192.168.1.254  YES manual  up  up

💻 Part 2: PC Configuration
Step 1: Assign IP Addresses

PC1

IP: 192.168.1.1

Subnet Mask: 255.255.255.0

PC2

IP: 192.168.1.2

Subnet Mask: 255.255.255.0

(Configured via Desktop → IP Configuration in Packet Tracer)

Step 2: Test Connectivity from PCs

From PC1 Command Prompt:

ping 192.168.1.253
ping 192.168.1.254
ping 192.168.1.2


From PC2 Command Prompt:

ping 192.168.1.254
ping 192.168.1.253
ping 192.168.1.1


✅ All pings should be successful
(Initial 80% success may occur due to ARP resolution)

🔍 Part 3: Verify Connectivity from Switches

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

🧠 What I Learned

A switch does not need an IP address to forward traffic, but it does need one for management

SVIs provide Layer 3 access to Layer 2 switches

Proper verification is just as important as configuration
