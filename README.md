# Subnet-design-part2
# README for IP Interfaces: Part 2


### Overview
In this lab, you will configure IP addresses for R2, R3, and R4 in Area 1 using the `10.10.11.0/24` block. Unlike the previous lab, R2, R3, and R4 are connected through different hubs, meaning they are not in the same broadcast or collision domain. Each pair of directly connected routers will require a unique subnet to ensure communication. Additionally, a `/28` subnet will be assigned to R4 (eth2) for future DHCP use.

---

### Configuration Requirements

1. **Subnet Assignment**:
   - Create four subnets to ensure that each pair of directly connected routers can communicate.
   - Ensure subnets do not overlap and are appropriately sized.
   - Use a `/28` subnet for R4 (eth2) for DHCP purposes.

2. **Subnet Table**:
   Complete the following table before configuration:

   | VM (interface) | IP Address | Network Address | Broadcast Address | Range (usable addresses) |
   |----------------|------------|-----------------|-------------------|--------------------------|
   | R2 (eth1)      |            |                 |                   |                          |
   | R3 (eth0)      |            |                 |                   |                          |
   | R2 (eth2)      |            |                 |                   |                          |
   | R4 (eth1)      |            |                 |                   |                          |
   | R3 (eth1)      |            |                 |                   |                          |
   | R4 (eth0)      |            |                 |                   |                          |
   | R4 (eth2)      |            |                 |                   |                          |

---

### Part 1: Configuring Network Interfaces

1. **Using vtysh**:
   - Open a terminal and enter the following commands:
     ```bash
     sudo su
     vtysh
     configure terminal
     interface <interface name> # Replace <interface name> with eth0, eth1, or eth2
     ip address x.x.x.w/<subnet mask> # Replace x.x.x.w with the assigned IP
     end
     write
     exit
     ```
   - Verify your configuration with:
     ```bash
     ifconfig
     ```

2. **Save Configurations**:
   - Use the `write` command in `vtysh` to save your configurations permanently.

---

### Part 2: Questions

1. **Why must subnets not overlap?**  
   Discuss the potential issues caused by overlapping subnets and provide an example.

2. **Adding a New Router (R5)**:  
   If R5 is added to the hub between R3 and R4, explain whether the IP subnets on R3 and R4 would need to be reconfigured for R5 to communicate.

3. **Wireshark Analysis**:  
   - Run Wireshark on R2 (eth1).
   - Ping R3 (eth1) from R2 and identify the type of packet used in the ping. Explain why R2 cannot reach R3 (eth1).

4. **Comparison of Wireshark Results**:  
   - Ping R3 (eth0) from R2 (eth1) and compare the Wireshark results to the previous ping.

---

### Submission Requirements

1. **Configuration Files**:
   - Screenshot of `/etc/frr/frr.conf` from R2, R3, and R4.

2. **Subnet Table**:
   - Completed table with all subnet details.

3. **Ping Tests**:
   - Screenshot showing successful ping between R2, R3, and R4.

4. **ARP Tables**:
   - Screenshot of ARP tables on R2, R3, and R4.

5. **Question Answers**:
   - Written responses to Part 2 questions.

---

### Notes
- Ensure subnets are non-overlapping and appropriately sized for each connection.
- Verify connectivity between all routers before capturing screenshots.
- Save all configurations to avoid losing changes upon reboot.

Good luck!
