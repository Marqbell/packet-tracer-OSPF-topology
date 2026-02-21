# packet-tracer-OSPF-topology
CCNA multi-area ospf practice lab
Overview

Designed and implemented a multi-area OSPF topology using Cisco Packet Tracer to simulate an enterprise WAN environment with backbone and branch segmentation.

Topology

4 Routers (Area 10, Area 0, Area 20)

2 LAN segments

Loopback interfaces for router ID stability

ABR configuration between areas

Key Implementations

Configured router IDs manually

Implemented passive interfaces on LAN-facing ports

Assigned structured /30 WAN addressing

Configured multi-area OSPF with correct backbone connectivity

Verified adjacency states (FULL)

Validated routing tables and inter-area route propagation

Troubleshooting Performed

Identified and resolved duplicate IP address conflict

Diagnosed failed pings due to missing routing entries

Verified interface states using show ip interface brief

Validated OSPF neighbors using show ip ospf neighbor

Confirmed route installation using show ip route

Corrected incorrect OSPF network statements and area assignments

Key Learning Outcomes

Understood dynamic routing next-hop resolution

Strengthened Layer 3 troubleshooting methodology

Reinforced importance of IP planning and structured addressing

Developed control-plane reasoning beyond basic configuration


Configuration Decisions & Troubleshooting Notes


Hostname Configuration

Each router hostname was manually configured to match the logical topology design (R1–R4).

Why:

Improves readability in multi-device environments

Reduces configuration errors during troubleshooting

Reflects real-world operational standards

Loopback Interface Implementation (Intentional Design)

Loopback interfaces were manually created on each router to simulate internal enterprise networks and provide stable logical endpoints.

Example:

interface loopback0
ip address 1.1.1.1 255.255.255.255


Purpose:

Simulates production-style internal routing endpoints

Demonstrates understanding of logical interfaces

Prepares topology for advanced routing scenarios (e.g., router-ID control, BGP, management addressing)

There were no connectivity issues related to loopbacks.

Duplicate IP Address Issue
Symptom

Unexpected behavior during connectivity testing.

Diagnosis

Used:

show ip interface brief


Discovered that two different interfaces had duplicate or overlapping IP addresses.

Root Cause

IP addressing conflict caused routing ambiguity.

Resolution

Corrected IP assignment

Revalidated addressing plan

Confirmed interface status (up/up)

Lesson:
Structured IP planning is critical. Duplicate IPs create unpredictable routing behavior.

Initial Ping Attempt Before Dynamic Routing

Before OSPF was fully configured, end-to-end pings failed.

Why This Happened

Routers only know:

Directly connected networks

Since no static routes or dynamic routing were configured yet, routers had no next-hop information for remote networks.

This was not a physical issue — it was a routing table limitation.

OSPF Implementation

After correcting IP addressing, OSPF was implemented across:

Area 10

Area 0 (Backbone)

Area 20

Each relevant interface was added to the correct OSPF area using network statements.

Example:

router ospf 1
network 10.0.12.0 0.0.0.3 area 10

Verification Process

Before testing connectivity, the following validations were performed:

show ip interface brief
show ip route
show ip ospf neighbor



Confirmed:

Interfaces were up/up

OSPF neighbors reached FULL state

Remote routes appeared in routing table (O / O IA entries)

Only after verifying the routing table contained remote networks was end-to-end ping tested again.

Result:
Full connectivity between LAN segments was successful.
<img width="937" height="1003" alt="Screenshot 2026-02-20 193504" src="https://github.com/user-attachments/assets/3d47ae71-faca-4d1d-a2c3-9c300f6f1580" />
<img width="952" height="1005" alt="Screenshot 2026-02-20 193203" src="https://github.com/user-attachments/assets/317ff8f9-b838-42ab-a186-63d9076dd064" />
<img width="945" height="1006" alt="Screenshot 2026-02-20 193027" src="https://github.com/user-attachments/assets/2f86b5b0-df28-40a3-8662-80933b8b44f9" />
<img width="947" height="1007" alt="Screenshot 2026-02-20 192954" src="https://github.com/user-attachments/assets/fc7377ab-2fc7-4589-8fce-aa7b0494ccab" />
<img width="951" height="1002" alt="Screenshot 2026-02-20 192920" src="https://github.com/user-attachments/assets/aafdf25e-4064-4f9a-aa39-70e2870a528b" />
<img width="951" height="1008" alt="Screenshot 2026-02-20 192732" src="https://github.com/user-attachments/assets/65209d43-53d8-4011-9554-1ec8575a6c51" />
<img width="948" height="1012" alt="Screenshot 2026-02-20 192334" src="https://github.com/user-attachments/assets/b36609e5-5e04-45c3-85a4-14a660ad6910" />
<img width="945" height="1012" alt="Screenshot 2026-02-19 R1" src="https://github.com/user-attachments/assets/d88110d7-32ab-43a9-acdd-47376d4faba6" />
<img width="1895" height="1005" alt="Screenshot 2026-02-19 ping failure dupicate ip and no shut" src="https://github.com/user-attachments/assets/b392b0b9-89c3-4895-9e38-3ff9cc0e7d17" />
<img width="957" height="1012" alt="Screenshot 2026-02-19 190139" src="https://github.com/user-attachments/assets/d612c218-4430-44d5-b3b6-be6b4c4c16da" />
<img width="951" height="1007" alt="Screenshot 2026-02-19 185908" src="https://github.com/user-attachments/assets/eac0b17f-c9fe-4e1a-b981-c260439ac06a" />
<img width="956" height="1002" alt="Screenshot 2026-02-19 185359" src="https://github.com/user-attachments/assets/de0a95de-a0c9-484e-92af-296b729c29e2" />
<img width="933" height="997" alt="Screenshot 2026-02-19 185222" src="https://github.com/user-attachments/assets/d3d37511-f7b6-42f1-b975-976960123084" />
<img width="948" height="1007" alt="Screenshot 2026-02-19 185139" src="https://github.com/user-attachments/assets/ec309b69-cae3-43c8-912c-efb7aeee6a65" />
<img width="933" height="881" alt="Screenshot 2026-02-19 185106" src="https://github.com/user-attachments/assets/1c396b26-5ec8-4caf-8a42-56789fb488f8" />
<img width="941" height="992" alt="Screenshot 2026-02-19 184232" src="https://github.com/user-attachments/assets/2ff83854-328c-4999-a05a-bc007e746e36" />
<img width="1892" height="995" alt="Screenshot 2026-02-19 184212" src="https://github.com/user-attachments/assets/4de4a860-48c7-44d2-91b5-faf10298f4e2" />
<img width="1883" height="996" alt="Screenshot 2026-02-19 184154" src="https://github.com/user-attachments/assets/e2ac4fef-d8b3-4aaf-9357-b1db69fef258" />
<img width="943" height="1002" alt="Screenshot 2026-02-19 183650" src="https://github.com/user-attachments/assets/826278c9-d38b-440c-8247-d4e3697357f2" />
<img width="946" height="997" alt="Screenshot 2026-02-19 183618" src="https://github.com/user-attachments/assets/a212ba26-78e5-404e-87c2-81b8b1fdf33b" />
<img width="952" height="1001" alt="Screenshot 2026-02-19 183532" src="https://github.com/user-attachments/assets/cc11850d-00bb-4be1-bbfe-5dbded525b77" />
<img width="935" height="996" alt="Screenshot 2026-02-19 183504" src="https://github.com/user-attachments/assets/04fc968f-d8e7-4ef7-853f-d9e87e050c42" />
<img width="952" height="1012" alt="Screenshot 2026-02-19 183114" src="https://github.com/user-attachments/assets/30fc7259-e07a-4995-baf5-1c25331addc0" />
<img width="951" height="1011" alt="Screenshot 2026-02-19 181950" src="https://github.com/user-attachments/assets/fece56a8-014f-4986-978f-d14d29595ae4" />
<img width="952" height="1007" alt="Screenshot 2026-02-19 181725" src="https://github.com/user-attachments/assets/7b83a15f-6a30-42d8-82ea-7ea4a4bbd2a6" />
<img width="1918" height="1010" alt="Screenshot TOPOLOGY" src="https://github.com/user-attachments/assets/b12def7f-ab0c-4f62-ba14-05fc9d8b1e79" />
<img width="947" height="1006" alt="Screenshot 2026-02-20 193557" src="https://github.com/user-attachments/assets/7c2c7355-53d3-4311-a69d-2d22167c579e" />

This lab reinforced the importance of verifying routing tables before testing connectivity and demonstrated the relationship between next-hop logic and dynamic routing protocols.
