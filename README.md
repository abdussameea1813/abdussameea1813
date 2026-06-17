<div align="center">

# Abdussameea Patel
### IT Support Technician · Help Desk L1/L2 · Network & Infrastructure

[![LinkedIn](https://img.shields.io/badge/LinkedIn-abdussameea--patel-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/abdussameea-patel)
[![Email](https://img.shields.io/badge/Email-abdussameea1%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:abdussameea1@gmail.com)
[![Location](https://img.shields.io/badge/Hamilton%2C_ON-Available_for_on--site_work-1B3A6B?style=flat&logo=google-maps&logoColor=white)]()
[![Work Auth](https://img.shields.io/badge/Canada-Authorized_to_Work-red?style=flat)]()

</div>

---

## Who I Am

IT Support Technician based in Hamilton, Ontario. I hold a **Computer Systems Technician diploma from Mohawk College** (Dec 2025) and **2.5+ years of Tier 1/2 help desk experience** owning tickets end-to-end — hardware, software, OS, and network issues.

I don't wait for a job to give me lab time. The two projects pinned below were built from scratch, broken on purpose, fixed, and documented — because that's how you actually learn.

**Class G driver's licence** — fully mobile for on-site MSP work across Ontario.

---

## Technical Skills

| Domain | Skills |
|--------|--------|
| **Help Desk** | Tier 1/2 support · ticket triage · SLA prioritization · escalation with written context · remote & deskside |
| **Active Directory** | User/group/OU management · password resets · account provisioning & deprovisioning · GPO creation & enforcement |
| **Windows** | Windows 10/11 config & troubleshooting · Windows Server 2022 · imaging · driver & update management |
| **Microsoft 365** | Outlook · Teams · OneDrive · account provisioning · permissions · license management · MFA |
| **Networking** | TCP/IP · DNS · DHCP · VLANs · OSPF · HSRP · NAT/PAT · ACLs · LAN/Wi-Fi troubleshooting · Cisco IOS CLI |
| **Hardware** | Desktop/laptop diagnostics · component replacement · printer & peripheral setup · workstation deployment |
| **Virtualization** | VirtualBox · Windows Server 2022 DC deployment · Hyper-V concepts |
| **Documentation** | Incident logs · SOPs · knowledge base articles · onboarding checklists · user-facing guides |

---

## Lab Projects

### 🏢 Lab 1 — Multi-Site Enterprise Network Simulation
> **Cisco Packet Tracer · OSPF · HSRP · ACLs · DHCP Relay · NAT/PAT**

[![View Lab](https://img.shields.io/badge/View_Lab-enterprise--network--lab-1B3A6B?style=flat&logo=github&logoColor=white)](https://github.com/abdussameea1813/enterprise-network-lab)

Built a fully operational 3-site enterprise network — Head Office, Branch, and Data Center — using Cisco 2911 routers and a 3560 L3 switch. Every protocol was configured, deliberately broken, and fixed.

**What was built:**

- **OSPF Area 0** across all 3 sites via serial WAN links — verified with `show ip route` (O entries for all remote networks) and `show ip ospf neighbor` (all adjacencies in FULL state)
- **HSRP gateway redundancy** at HQ — virtual IP `192.168.10.254`, priority 110, preempt enabled. Tested failover by killing the active router: traffic recovered in under 3 seconds, zero manual intervention
- **Named extended ACL (PROTECT-DC)** — permits HQ traffic to Data Center, denies Branch. Applied inbound on WAN interface. Verified with live hit counters: 12 deny matches, 8 permit matches
- **DHCP Relay** via `ip helper-address` — Branch PCs auto-assign IPs from central HQ server across the WAN, zero static config at Branch
- **NAT PAT** on HQ-Router — all 3 sites reach internet through one public IP. Default route redistributed via OSPF so Branch and DC learn it automatically

**Real troubleshooting log:**

| Problem | Root Cause | Fix |
|---------|-----------|-----|
| ACL not blocking Branch | ACL applied to wrong interface | Moved to `serial 0/3/0 inbound` |
| NAT not translating Branch traffic | Serial0/3/0 missing `ip nat inside` | Added to all internal interfaces |
| Default route not reaching Branch | `default-information originate` missing | Added to OSPF process on HQ-Router |
| DHCP relay not working | ip helper-address set, but scope missing | Created BranchPool scope on HQ-Server |

---

### 🖥️ Lab 2 — Windows Server 2022 Active Directory Infrastructure
> **Windows Server 2022 · AD DS · DNS · DHCP · GPO · VirtualBox**

[![View Lab](https://img.shields.io/badge/View_Lab-home--lab--network-1B3A6B?style=flat&logo=github&logoColor=white)](https://github.com/abdussameea1813/home-lab-network)

Deployed a fully functional corporate domain environment from a bare Windows Server install — replicating the exact infrastructure an MSP technician manages daily.

**What was built:**

- **Domain Controller (DC01)** — promoted from scratch, new forest `lab.local`, AD DS + DNS + DHCP roles installed and configured
- **OU structure, users, security groups** — custom OUs (Admins), domain users (jdoe), global security groups (GG-IT-Admins, GG-Staff), group membership managed via ADUC
- **DHCP scope** `192.168.10.100–.200` with scope options (router, DNS, domain name) — PC01 auto-assigned IP, lease verified in DHCP console and `ipconfig /all`
- **Group Policy** — created `Block Control Panel` GPO linked to `lab.local`, enforced via `gpupdate /force`, verified blocked access on domain client
- **Cisco Packet Tracer VLAN topology** — router-on-a-stick inter-VLAN routing, VLAN 10 (Servers) and VLAN 20 (Clients), trunk uplinks — validated 0% packet loss end-to-end

**Real troubleshooting log:**

| Problem | Root Cause | Fix |
|---------|-----------|-----|
| `nslookup lab.local` timing out | IPv6 DNS taking priority over IPv4 | Disabled IPv6 on PC01 NIC, flushed DNS cache |
| Ping to DC01 failing | Windows Firewall blocking ICMP | Added inbound ICMP allow rule via `netsh advfirewall` |
| DNS still failing after firewall fix | DNS listening on IPv6 `::1` not IPv4 | Configured DNS Manager to listen on `192.168.10.10` only |
| Inter-VLAN ping failing | Trunk port not correctly configured | Reconfigured trunk on correct port after `show interfaces status` |

---

## Experience

**IT Support Technician** — Reytax IT Services *(deployed to Munshi School)*, India · Jan 2021 – Aug 2023
- Sole Tier 1/2 help desk contact for 200+ staff — hardware, software, OS, printer, and network issues
- AD account management, workstation configuration, access provisioning, onboarding checklists
- Authored troubleshooting guides that measurably reduced repeat incidents

**Receiver & Stock Associate** — Walmart Canada, ON · Nov 2023 – Present
- Bridging to full-time IT career while in Canada

---

## Education & Certifications

🎓 **Computer Systems Technician** — Mohawk College, Hamilton, ON · Dec 2025

🎓 **Computer Engineering Diploma** — Gujarat Technological University, India · May 2021

📋 **CompTIA A+** — In Progress · Network+ & CCNA on roadmap

---

## Currently

- 📍 Based in Hamilton, ON — available for on-site work across Ontario
- 🔍 Actively seeking IT Support / Help Desk / NOC Analyst roles
- 📚 Studying for CompTIA A+ · Building toward Network+

---

<div align="center">
<sub>Class G Driver's Licence · Authorized to work in Canada · Bilingual: English & Gujarati</sub>
</div>
