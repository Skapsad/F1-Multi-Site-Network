# 🏎️ F1 Multi-Site Network Infrastructure

**Enterprise Network Design & Simulation | Cisco Packet Tracer**

## Project Overview

This project simulates a multi-site enterprise network designed for a fictional Formula 1 racing team, connecting its headquarters and race circuit through a centralized core infrastructure.

The objective was to design, configure, secure, and troubleshoot a network capable of supporting multiple departments, centralized network services, secure remote administration, and simulated internet connectivity.

The infrastructure was developed using Cisco Packet Tracer.

## Network Topology

F1 Network Topology

The network consists of:

- **Headquarters:** Engineering, Management, IT, and Server departments.
- **Race Circuit:** Race Engineering, Garage Operations, and Guest networks.
- **Core Infrastructure:** Central routing between both sites and the external ISP.
- **Simulated ISP:** External network connectivity and a web server.

The infrastructure uses three internal Cisco routers, four switches, ten client PCs, two servers, and one simulated ISP router.

## Technologies Implemented

### 1. VLANs and Inter-VLAN Routing

Configured seven VLANs to logically separate departments and organize network traffic.

| VLAN | Department | Network |
|---|---|---|
| 10 | HQ Engineering | 192.168.10.0/24 |
| 20 | HQ Management | 192.168.20.0/24 |
| 30 | HQ IT | 192.168.30.0/24 |
| 40 | Circuit Race Engineering | 192.168.40.0/24 |
| 50 | Circuit Garage | 192.168.50.0/24 |
| 60 | Circuit Guest | 192.168.60.0/24 |
| 70 | HQ Servers | 192.168.70.0/24 |

Implemented router-on-a-stick using IEEE 802.1Q trunking for inter-VLAN routing.

### 2. Multi-Area OSPF

Configured OSPF to enable dynamic routing between headquarters, the core, and the race circuit.

- **Area 0:** Backbone connections.
- **Area 1:** Headquarters LANs.
- **Area 2:** Circuit LANs.
- Verified FULL OSPF neighbor adjacencies.
- Verified inter-area route advertisements.
- Advertised a default route from CORE using OSPF.

### 3. EtherChannel and Switching

Implemented LACP EtherChannel between switch pairs at both sites.

- Combined physical Ethernet connections into logical Port-channel interfaces.
- Configured VLAN trunking.
- Verified EtherChannel functionality and VLAN connectivity.

### 4. Centralized DHCP

Configured a centralized DHCP server at headquarters.

- Automatic IP address allocation for six client VLANs.
- DHCP relay using `ip helper-address`.
- Distribution of IP addresses, subnet masks, default gateways, and DNS server settings.
- Verified DHCP operation across both sites.

### 5. Access Control Lists

Implemented ACL-based security restrictions.

**Guest Network Isolation**
- Restricted Circuit Guest access to internal `192.168.0.0/16` networks.
- Allowed connectivity to the simulated external network.

**Management Protection**
- Blocked ICMP echo requests from HQ Engineering to HQ Management.

**SSH Access Control**
- Restricted SSH administration to the HQ IT subnet.

### 6. Secure Remote Administration

Configured SSH version 2 on seven internal network devices.

- Local administrator authentication.
- RSA key generation.
- SSH-only VTY access.
- IT-subnet-only remote management.
- Remote administration of routers and switches.

The simulated ISP router was intentionally excluded from internal administrative access.

### 7. NAT/PAT

Configured PAT on R4-CORE.

- Translated internal private addresses to the CORE external-facing IP address.
- Enabled multiple internal devices to share one external IP.
- Configured a static default route toward the ISP.
- Advertised the default route through OSPF.
- Verified NAT translation entries and external connectivity.

### 8. DNS and Internal Web Services

Configured centralized DNS and HTTP services.

- Internal DNS records using `f1team.local`.
- Internal intranet hosted on HQ-SERVER.
- Hostname resolution between HQ and Circuit.
- Verified intranet access from authorized networks.

## Network Security

Implemented foundational network security controls:

- Departmental segmentation using VLANs.
- ACL-based traffic restrictions.
- Guest network isolation.
- SSH-only remote administration.
- Source-based management access restrictions.
- Separation of internal infrastructure from the simulated ISP.

## Testing and Verification

| Test | Result |
|---|---|
| Inter-VLAN connectivity | Passed |
| HQ-to-Circuit connectivity | Passed |
| OSPF neighbor establishment | Passed |
| DHCP address allocation | Passed |
| EtherChannel operation | Passed |
| Guest VLAN isolation | Passed |
| SSH authentication | Passed |
| Unauthorized SSH restrictions | Passed |
| NAT/PAT translations | Passed |
| Simulated internet connectivity | Passed |
| Internal DNS resolution | Passed |
| F1 intranet access | Passed |

**Verification commands included:**

- `show ip route`
- `show ip ospf neighbor`
- `show vlan brief`
- `show etherchannel summary`
- `show access-lists`
- `show ip ssh`
- `show ip nat translations`
- `ping`
- `tracert`

## Tools and Equipment

**Simulation Platform:** Cisco Packet Tracer

**Equipment:**
- 4 Cisco 2911 routers, including simulated ISP
- 4 Cisco switches
- 10 client PCs
- 2 servers

**Technologies:** TCP/IP, VLANs, 802.1Q, LACP, OSPF, DHCP, DNS, HTTP, SSH, ACLs, NAT/PAT.

## Challenges and Troubleshooting

During development, I encountered and resolved several networking issues:

- Incorrect DHCP default gateway assignments.
- OSPF routing and default-route advertisement issues.
- Switch management IP and SSH connectivity problems.
- ACL configuration and access verification.
- NAT/PAT connectivity troubleshooting.
- Recovery and restoration of network configurations following a Packet Tracer crash.

These challenges provided hands-on experience in diagnosing network problems, validating configurations, and restoring services.

## Project Scope

This project is an educational network simulation, not a production Formula 1 infrastructure deployment.

The simulated external network uses documentation IP ranges, and the security configurations demonstrate foundational enterprise networking concepts.

## Future Improvements

- Centralized syslog and network monitoring.
- NTP synchronization.
- Redundant links and routing failover.
- Dedicated management VLANs.
- Advanced firewall policies.
- Site-to-site VPN connectivity.

## Project Objective

This project was developed to strengthen practical skills in enterprise networking, routing, switching, network security, and troubleshooting.

It also supports my long-term goal of pursuing a career in motorsport IT infrastructure, particularly within Formula 1.

---

**Project Status:** Completed

**Platform:** Cisco Packet Tracer

**Focus:** Enterprise Networking | Network Security | Motorsport IT
