# Newtork-Design-for-a-Cloud-Company
Designed and implemented a secure, high-availability enterprise campus network in Cisco Packet Tracer featuring dual Cisco ASA firewalls (Inside/Outside/Server Farm), multi-layer switching with HSRP and OSPF, centralized WLC wireless management, and integrated VoIP telephony.

🌐 Enterprise Campus Network System

A complete, high-availability enterprise network system designed and implemented in Cisco Packet Tracer. It features a hierarchical multi-floor architecture with dual ASA firewalls, inter-VLAN routing, redundant gateways, centralized wireless management, and VoIP telephony. I built this project for learning purposes, focusing primarily on enterprise security, failover redundancy, and scalable traffic segmentation.

🛠️ Technologies & Protocols

.Cisco Packet Tracer

.Cisco IOS CLI

.OSPF (Open Shortest Path First)

.HSRP (Hot Standby Router Protocol)

.LACP (EtherChannel)

.STP (PortFast & BPDU Guard)

.Cisco ASA 5506-X Firewalls

.NAT / PAT & ACLs

.WLC (Wireless LAN Controller)

.VoIP (Cisco IP Telephony)

🦄 Features

Here's what this network architecture includes:

VLAN Segmentation: Traffic is isolated across dedicated subnets including Management (VLAN 10), Data LAN (VLAN 20), Wireless (VLAN 50), VoIP (VLAN 70), Server Farm (VLAN 90), and a Black Hole VLAN (VLAN 999) for unused ports.

High Availability & Redundancy: Dual multilayer core switches configured with HSRP ensure automatic gateway failover if a primary link or switch goes down.

Link Aggregation: LACP EtherChannel bundles physical links between access and core switches to increase bandwidth and prevent Spanning Tree loops.

Perimeter Security & DMZ: Dual Cisco ASA 5506 firewalls segment the network into Inside, Outside, and DMZ security zones with stateful packet inspection for ICMP, HTTP, and DNS.

Centralized Wireless Management: A Cisco Wireless LAN Controller (WLC) manages lightweight access points across multiple departments using CAPWAP tunnels.

IP Telephony (VoIP): Dedicated Cisco 2811 Voice Gateways provide automated extension provisioning and dial peers for internal phone communication across floors.

⌨️ Useful CLI Verification Commands:

.Speed up your network testing and troubleshooting with these Cisco IOS commands:

.Verify VLANs & Ports: show vlan brief and show interfaces trunk

.Check EtherChannel Status: show etherchannel summary

.Verify HSRP Failover: show standby brief

.Inspect Routing Table & OSPF: show ip route and show ip ospf neighbor

.Check Firewall NAT & Security Zones: show run nat and show nameif

.Test Remote Management: ssh -l admin <ip-address>

👩🏽‍🍳 The Process

I started by designing a hierarchical 3-tier topology (Core, Distribution, Access) across multiple building floors and calculating custom IPv4 subnets for each department. First, I focused on Layer 2 security—configuring trunk links, assigning access ports, disabling DTP (switchport nonegotiate), and shutting down unused ports in a black-hole VLAN.

Next, I made sure the network could survive hardware or link failures. I bundled inter-switch links using LACP EtherChannel and enabled STP PortFast and BPDU Guard on all edge ports. At the distribution layer, I configured SVIs (Switched Virtual Interfaces) and set up HSRP with active/standby priorities so end devices never lose their default gateway.

To handle internal and external traffic routing, I implemented dynamic multi-area OSPF across the multilayer switches and edge routers, along with ip helper-address relays so centralized DHCP servers could assign IPs across isolated VLANs.

For perimeter defense, I deployed Cisco ASA firewalls. I defined security levels for Inside (100), DMZ (50), and Outside (0) interfaces, wrote dynamic PAT rules for internet access, and modified the global modular policy framework to inspect ICMP and web traffic.

Finally, I integrated a Wireless LAN Controller (WLC) for department-specific Wi-Fi SSIDs and configured a Voice Router with telephony-service to register IP phones. Along the way, I tested every implementation step with continuous pings, traceroutes, and simulation mode packet tracing.

📚 What I Learned

During this project, I picked up practical network engineering skills and a much deeper understanding of how enterprise protocols interact in production environments.

🧠 HSRP & Gateway Redundancy:

Logical Thinking: Configuring standby groups and preemption taught me how networks maintain uptime when hardware fails, and how asymmetric routing can happen if STP root bridges don't align with HSRP active routers.

📐 Subnetting & VLAN Architecture:

Accuracy: Designing overlapping-free subnets for Data, Voice, Management, and DMZ zones required strict IP planning and careful wildcard mask calculations.

Traffic Isolation: I learned how to combine voice and data VLANs on a single switch port while keeping broadcast domains completely separate.

🛡️ Cisco ASA Firewall & Security Zones:

Security Policy Design: Working with Cisco ASA appliances taught me how security levels dictate traffic flow by default, and how to use Object Network NAT and Access Control Lists (ACLs) to safely expose DMZ servers without compromising the internal LAN.

🔗 Link Aggregation & Spanning Tree:

Loop Prevention: I gained hands-on experience bundling physical ports into logical Port-Channels using channel-group mode active (LACP) and protecting access switches against rogue switches with spanning-tree bpduguard enable.

📡 Centralized Wireless & VoIP Integration:

Service Convergence: Configuring option 150 on DHCP pools for IP phones and binding lightweight APs to a WLC showed me how modern enterprise networks converge data, voice, and wireless traffic onto a single physical infrastructure.

📈 Overall Growth:

Each phase of this topology helped me understand more about network resilience, defense-in-depth security, and systematic troubleshooting. It was much more than just connecting cables—it was about architecting a reliable system from the ground up.

💭 How can it be improved?

Implement 802.1X Port-Based Authentication with a RADIUS/TACACS+ AAA server.

Add IPv6 dual-stack routing (OSPFv3) across all internal VLANs.

Configure Site-to-Site IPsec VPN tunnels for secure remote branch connectivity.

Enable DHCP Snooping and Dynamic ARP Inspection (DAI) to prevent man-in-the-middle attacks on the LAN.

Set up an SNMP and Syslog monitoring server to log real-time device events and link state changes.

🚦 Running the Project

To explore and test the network simulation locally, follow these steps:

1.Download and install Cisco Packet Tracer (Version 8.2 or higher recommended).

2.Clone this repository to your local machine:

https://github.com/ashi77-debug/Newtork-Design-for-a-Cloud-Company/blob/main/project%202%20Cloud%20infrastructure.pkt


3.Open the .pkt topology file inside Cisco Packet Tracer.

4.Wait ~30 seconds (or press Alt + D in Realtime mode) for STP, EtherChannel, and OSPF adjacencies to converge.

5.Open any PC's Command Prompt or Web Browser to test end-to-end connectivity, SSH access, and DMZ web server resolution.


Video Format



https://github.com/user-attachments/assets/bc6bb3bc-af42-4292-9265-b9c46e99f868







