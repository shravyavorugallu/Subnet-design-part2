# Subnet-design-part2
### Lab Project: IP Interfaces - Part 2

---

## Project Overview
This lab project involves configuring IP addresses for R2, R3, and R4 in Area 1. Each router is connected through separate hubs, ensuring distinct broadcast and collision domains. The goal is to set up non-overlapping subnets for direct communication between each pair of connected routers.

---

## Objectives
- Assign IP addresses from the 10.10.11.0/24 subnet to R2, R3, and R4.
- Configure four unique subnets for the directly connected router pairs.
- Reserve a /28 subnet on R4 (eth2) for future DHCP assignments.

---

## Lab Tasks

### 1. **Subnet Calculation and Address Assignment**
   - Determine appropriate subnets for the router interfaces:
     - Each subnet should accommodate the two connected routers.
     - Ensure no overlapping between subnets.
   - Fill in the IP address table:

     | VM (Interface) | IP Address | Network Address | Broadcast Address | Range (Usable Addresses) |
     |----------------|------------|-----------------|-------------------|--------------------------|
     | R2 (eth1)      |            |                 |                   |                          |
     | R3 (eth0)      |            |                 |                   |                          |
     | R2 (eth2)      |            |                 |                   |                          |
     | R4 (eth1)      |            |                 |                   |                          |
     | R3 (eth1)      |            |                 |                   |                          |
     | R4 (eth0)      |            |                 |                   |                          |
     | R4 (eth2)      |            |                 |                   |                          |

---

### 2. **Configuring Network Interfaces**
   - Use `vtysh` on each router to configure the interfaces:
     ```bash
     sudo su
     vtysh
     configure terminal
     interface <interface name>
     ip address <IP Address>/<Subnet Mask>
     end
     write
     exit
     ```
   - Verify the configuration using:
     ```bash
     ifconfig
     ```

---

### 3. **Testing Connectivity**
   - Ping between directly connected routers to verify communication:
     ```bash
     ping <Target Router IP Address>
     ```
   - Use `traceroute` to confirm routing paths:
     ```bash
     traceroute <Target Router IP Address>
     ```

---

### 4. **Wireshark Analysis**
   - Run Wireshark on R2 (eth1) to capture packets.
   - Ping R3 (eth1) from R2 and observe the packet type (e.g., ICMP).
   - Analyze why R2 cannot reach R3 (eth1) directly.
   - Compare results when pinging R3 (eth0) from R2 (eth1).

---

## Deliverables
1. Completed IP address table with subnet details.
2. Screenshot of the configuration files from R2, R3, and R4.
3. Screenshot showing successful pings between all routers.
4. Wireshark capture showing ICMP packets.
5. Observations on connectivity and routing behavior.

---

## Notes
- Ensure subnets do not overlap to avoid routing conflicts.
- Save configurations to prevent data loss after reboots.
- Use `arp` to verify address resolution on each router.

---

