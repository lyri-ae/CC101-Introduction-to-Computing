# SORSOGON STATE UNIVERSITY

**College of Information and Communications Technology**

*Bulan Campus, Zone 8, Bulan, Sorsogon*

**Email Address:** cict@sorsu.edu.ph | **Tel. No.:** 056 311-0103

---

## CC 101 - Introduction to Computing
### "Know Your Network Settings": Exploring Windows 11 Network Configuration Tools

* **Name:** Angel Lyra A. Escandor
* **Block:** BSCS 1-1
* **Computer Unit Used:** MSI DESKTOP
* **Date:** October 21, 2026

---

### I. Objectives

At the end of this activity, you should be able to:

* Locate network adapter information using Windows 11 Settings, the Control Panel, Command Prompt (CMD), and PowerShell.
* Use `ipconfig`, `getmac`, `hostname`, `ping`, `netstat`, `route print`, and `systeminfo` in CMD, and `Get-NetAdapter`, `Get-NetIPAddress`, and `Test-Connection` in PowerShell.
* Interpret a sample `ipconfig /all` output from a networked computer: identify its IP address, subnet mask, default gateway, and DNS servers, and classify the address as public or private.
* Relate each tool and finding to the layer of the OSI model where it works.
* Design a simple network and IP address plan for the computer laboratory.

---

### II. Materials Needed

* A computer running Windows 11
* This worksheet
* Week 6 lecture notes for reference on IP addresses, protocols, the OSI model, and network devices

---

### III. Background

A computer does not need to be connected to a network to have network settings. Every PC has one or more network adapters (NICs), each with a permanent MAC address, and Windows always runs the TCP/IP software, including the loopback address `127.0.0.1` (IPv4) and `::1` (IPv6) that the computer uses to talk to itself. Windows 11 lets you inspect these settings in four places: the Settings app, the classic Control Panel, Command Prompt (CMD), and PowerShell. In this activity, you will explore all four on your own unit, observe how Windows behaves when no network is available, and then analyze a sample configuration taken from a computer that is connected to a network.

---

### IV. Procedure

> **Reminder:** This is a viewing activity. Do not change, disable, or reset any network setting. Close every dialog with Cancel. Record values exactly as Windows shows them.

#### Part A - Windows 11 Settings

1. Press $\text{Windows} + \text{I}$ to open Settings, then click **Network & internet**. Write down the connection status shown at the top of the page.
2. Click **Advanced network settings**. Under **Network adapters**, note every adapter listed and whether each one is enabled or disconnected.
3. Scroll down and click **Hardware and connection properties**. For each adapter, record its Name, Description, Physical address (MAC), and Status in Table 1.

#### Part B - Control Panel (Network Connections)

4. Press $\text{Windows} + \text{R}$, type `ncpa.cpl`, and press **Enter**.
5. Right-click your Ethernet adapter and choose **Properties**. List the items checked under *"This connection uses the following items"* in Table 2.
6. Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**. Record whether the computer is set to obtain an IP address automatically (DHCP) or manually, and the same for DNS. Click Cancel.

#### Part C - Command Prompt (CMD)

7. Open `cmd` and run: `hostname`, `getmac /v`, `ipconfig /all`. Record results in Table 3.
8. Test the computer's loopback address: `ping 127.0.0.1` and `ping localhost`.
9. Test remote connectivity and domain lookup: `ping 8.8.8.8` and `nslookup google.com`.
10. Check active listening ports and routes: `netstat -an | findstr LISTENING` and `route print -4`.
11. Run `systeminfo` to inspect network card details.

#### Part D - PowerShell

12. Open Terminal or PowerShell and run:
    * `Get-NetAdapter`
    * `Get-NetIPAddress -AddressFamily IPv4 | Format-Table InterfaceAlias, IPAddress, PrefixLength`
    * `Test-Connection 127.0.0.1 -Count 4`
    * `Get-NetTCPConnection -State Listen | Select-Object -First 5 LocalAddress, LocalPort`

#### Part E - Analyze a Networked Computer

13. Study the provided `ipconfig /all` sample output and answer the analysis questions in Table 5.

```text
Sample Output 1. ipconfig /all (excerpt) from a networked PC

Host Name . . . . . . . . . . . . : CICT-LAB-PC07
Ethernet adapter Ethernet:
   Description . . . . . . . . . : Realtek PCIe GbE Family Controller
   Physical Address. . . . . . . : 3C-52-82-A1-7F-09
   DHCP Enabled. . . . . . . . . : Yes
   Link-local IPv6 Address . . . : fe80::8c2d:4a1f:93b2:61e5%12 (Preferred)
   IPv4 Address. . . . . . . . . : 192.168.10.37 (Preferred)
   Subnet Mask . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . : Wednesday, October 14, 2026 8:02:15 AM
   Lease Expires . . . . . . . . : Thursday, October 15, 2026 8:02:15 AM
   Default Gateway . . . . . . . : 192.168.10.1
   DHCP Server . . . . . . . . . : 192.168.10.1
   DNS Servers . . . . . . . . . : 192.168.10.1, 8.8.8.8
```

#### Part F - Design a Network for Our Laboratory

14. Draw a simple star topology network with at least four PCs, one switch, one router (default gateway), one printer, and the ISP / Internet connection.
15. Assign each device a private IPv4 address from the network `192.168.10.0/24` and complete Table 6.

#### Part G - Optional / Bonus

16. In CMD, run `type C:\Windows\System32\drivers\etc\hosts` to view the hosts file and explain its relation to DNS.

---

### V. Data and Findings

#### Table 1. Network Adapters in Settings (Part A)

**Connection status shown on the Network & internet page:** Connected

| Adapter Name | Description | Physical Address (MAC) | Status |
| :--- | :--- | :--- | :--- |
| **Wi-Fi** | Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC | `CC:47:40:04:38:23` | Enabled |
| **Ethernet 2** | VirtualBox Host-Only Ethernet Adapter | `74:56:3C:7A:98:B6` | Enabled |
| **Ethernet** | Realtek PCIe GbE Family Controller | `0A:00:27:00:00:0F` | Enabled |

---

#### Table 2. Adapter Properties (Part B)

| Items Checked Under "This connection uses the following items" | Item Checked (continued) |
| :--- | :--- |
| Client for Microsoft Networks | Microsoft LLDP Protocol Driver |
| File and Printer Sharing for Microsoft Networks | Internet Protocol Version 6 (TCP/IPv6) |
| VirtualBox NDIS6 Bridged Networking Driver | Link-Layer Topology Discovery Responder |
| QoS Packet Scheduler | Link-Layer Topology Discovery Mapper I/O Driver |
| Internet Protocol Version 4 (TCP/IPv4) | |

| TCP/IPv4 Setting | Automatic or Static? |
| :--- | :--- |
| **IP address** | Automatic |
| **DNS server address** | Automatic |

---

#### Table 3. Command Prompt Results (Part C)

| Command / Item | Your Findings | OSI Layer |
| :--- | :--- | :--- |
| `hostname` | `DESKTOP-93QA1LV` | Layer 7 - Application |
| `getmac /v` | **MAC Address:**<br>`CC-47-40-04-3A-23`<br>`74-56-3C-7A-98-B6`<br>`0A-00-27-00-00-0F`<br><br>**Transport Name:**<br>`Media disconnected`<br>`\Device\Tcpip_{10842D47-5788-4897-872E-FBAC9B8171D}`<br>`\Device\Tcpip_{AED96CB3-B4C4-42A4-88E0-C1D2796E9CB1}` | Layer 2 - Data Link |
| `ipconfig /all` | **Ethernet State:** Connected (Active)<br>**DHCP Enabled:** Yes | Layer 2 - Data Link / Layer 7 - Application |
| `ping 127.0.0.1` | Pinging `127.0.0.1` with 32 bytes of data:<br>Reply from `127.0.0.1`: bytes=32 time<1ms TTL=128<br>Reply from `127.0.0.1`: bytes=32 time<1ms TTL=128<br>Reply from `127.0.0.1`: bytes=32 time<1ms TTL=128<br>Reply from `127.0.0.1`: bytes=32 time<1ms TTL=128 | Layer 3 - Network |
| `ping localhost` | Pinging `DESKTOP-93QA1LV` [`::1`] with 32 bytes of data:<br>Reply from `::1`: time<1ms<br>Reply from `::1`: time<1ms<br>Reply from `::1`: time<1ms<br>Reply from `::1`: time<1ms | Layer 3 - Network |
| `ping 8.8.8.8` | Pinging `8.8.8.8` with 32 bytes of data:<br>Reply from `8.8.8.8`: bytes=32 time=15ms TTL=115<br>Reply from `8.8.8.8`: bytes=32 time=15ms TTL=115<br>Reply from `8.8.8.8`: bytes=32 time=15ms TTL=115<br>Reply from `8.8.8.8`: bytes=32 time=15ms TTL=115<br><br>Ping statistics for 8.8.8.8:<br>Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),<br>Approximate round trip times in milli-seconds:<br>Minimum = 15ms, Maximum = 15ms, Average = 15ms | Layer 3 - Network |
| `nslookup google.com` | **Server:** gpon.net<br>**Address:** `fe80::1`<br><br>Non-authoritative answer:<br>**Name:** google.com<br>**Addresses:** `2404:6800:4017:80c::200e`, `172.217.26.238` | Layer 7 - Application |
| `netstat -an` (3 LISTENING) | `TCP 0.0.0.0:135 0.0.0.0:0 LISTENING`<br>`TCP 0.0.0.0:445 0.0.0.0:0 LISTENING`<br>`TCP 0.0.0.0:5040 0.0.0.0:0 LISTENING` | Layer 4 - Transport |
| `route print -4` | **Netmask for 127.0.0.0:** `255.0.0.0` | Layer 3 - Network |
| `systeminfo` | `3 NIC(s) Installed.` | Layer 2 - Data Link |

---

#### Table 4. PowerShell Results (Part D)

| Command | What It Showed | Matches CMD? (Y/N) |
| :--- | :--- | :---: |
| `Get-NetAdapter` | **Name:** Wi-Fi, Ethernet 2, Ethernet<br>**Status:** Disconnected, Up, Up<br>**MacAddress:** `CC-47-40-04-3A-23`, `0A-00-27-00-00-0F`, `74-56-3C-7A-98-B6`<br>**LinkSpeed:** 1 Mbps, 1 Gbps, 1 Gbps | Y |
| `Get-NetIPAddress` | **InterfaceAlias:** Ethernet 2 \| **AddressFamily:** IPv4 \| **PrefixLength:** 16<br>**InterfaceAlias:** Ethernet \| **AddressFamily:** IPv4 \| **PrefixLength:** 24<br>**InterfaceAlias:** Wi-Fi \| **AddressFamily:** IPv4 \| **PrefixLength:** 16 | Y |
| `Test-Connection 127.0.0.1` | **Source:** `DESKTOP-93QA1LV`<br>**Destination:** `127.0.0.1`<br>**IPv4Address:** `169.254.247.111`<br>**IPv6Address:** `fe80::8349:b440:c309:f7c2%15`<br>**Bytes:** 32 \| **Time (ms):** 0 | Y |
| `Get-NetTCPConnection -State Listen` | **LocalAddress:** `::` \| **LocalPort:** 49669 \| **OwningProcess:** 1416<br>**LocalAddress:** `::` \| **LocalPort:** 49668 \| **OwningProcess:** 3696 | N |

---

#### Table 5. Sample Output Analysis (Part E)

| Question | Your Answer |
| :--- | :--- |
| **IPv4 address of PC07** | `192.168.10.37` |
| **Subnet mask (and its /prefix)** | `255.255.255.0` or `/24` |
| **Default gateway, and what device it usually is** | `192.168.10.1` (usually a router) |
| **DNS servers** | `192.168.10.1`, `8.8.8.8` |
| **Was the address assigned by DHCP or set manually? How do you know?** | Assigned by DHCP because `DHCP Enabled` is set to `Yes`. |
| **Public or private? Which RFC 1918 range?** | Private IP address. It belongs to the `192.168.0.0/16` range defined by RFC 1918. |
| **IPv4 address of PC07 in binary (four octets)** | `11000000.10101000.00001010.00100101` |
| **MAC address, and the OSI layer where it is used** | `3C-52-82-A1-7F-09`, used at **OSI Layer 2 (Data Link Layer)**. |
| **How long is the DHCP lease?** | 24 hours (from Wednesday, Oct 14, 2026, 8:02:15 AM to Thursday, Oct 15, 2026, 8:02:15 AM). |
| **If the DHCP server failed, what kind of address would PC07 assign itself?** | An **APIPA** (Automatic Private IP Addressing) address in the `169.254.0.0/16` range (typically `169.254.x.x` with subnet mask `255.255.0.0`). |

---

#### Part F - Laboratory Network Design & Address Plan

```text
                     +-------------------+
                     |   ISP / Internet  |
                     +---------+---------+
                               |
                               v
                   +-----------------------+
                   | Router / Default Gateway |
                   |      192.168.10.1     |
                   +-----------+-----------+
                               |
                               v
                       +---------------+
                       |     Switch    |
                       +-------+-------+
                               |
      +----------------+-------+-------+----------------+
      |                |               |                |
      v                v               v                v
+-----------+    +-----------+   +-----------+    +-----------+
|    PC 1   |    |    PC 2   |   |    PC 3   |    |    PC 4   |
|192.168.10.2|   |192.168.10.3|  |192.168.10.4|   |192.168.10.5|
+-----------+    +-----------+   +-----------+    +-----------+
                               |
                               v
                       +---------------+
                       |    Printer    |
                       |  192.168.10.6 |
                       +---------------+

(Connect every device to the central switch using Ethernet cables)
```

*Figure 1. Proposed Laboratory Network Diagram (Part F)*

#### Table 6. IP Address Plan (Part F)

| Device | IPv4 Address | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- |
| **Router (gateway)** | `192.168.10.1` | `255.255.255.0` | N/A |
| **PC 1** | `192.168.10.2` | `255.255.255.0` | `192.168.10.1` |
| **PC 2** | `192.168.10.3` | `255.255.255.0` | `192.168.10.1` |
| **PC 3** | `192.168.10.4` | `255.255.255.0` | `192.168.10.1` |
| **PC 4** | `192.168.10.5` | `255.255.255.0` | `192.168.10.1` |
| **Printer** | `192.168.10.6` | `255.255.255.0` | `192.168.10.1` |

---

#### Part G Notes (Optional / Bonus)

The Windows `hosts` file is a plain text file located at `C:\Windows\System32\drivers\etc\hosts`. It maps hostnames directly to IP addresses manually. It relates to DNS because Windows checks the local `hosts` file before querying an external DNS server to resolve a domain name. This allows a computer to override DNS or access custom hosts locally without relying on external domain name servers.

---

### VI. Realization (Reflection)

1. **Even without a network connection, what network information did your computer still have? Why do you think it still has it?**
   Even without a network connection, my computer still had information like its IP address, MAC address, and loopback settings. These are stored locally because the hardware (NIC) and internal TCP/IP stack require them to function, run internal processes, and prepare for future network communication.

2. **Compare Settings, Control Panel, CMD, and PowerShell. Which tool did you find most useful for viewing network information, and why?**
   Settings and Control Panel offer graphical interfaces that are easy to navigate for general users. However, CMD and PowerShell provide much deeper detail instantly. I found CMD the most useful because entering a quick command like `ipconfig /all` immediately provides comprehensive network details on one screen without clicking through multiple menus.

3. **What did the messages from `ping 8.8.8.8` and `nslookup google.com` tell you? How would you use messages like these when troubleshooting a real network?**
   The `ping 8.8.8.8` command tests whether your device can reach a public server over the IP network, while `nslookup google.com` tests if your system can resolve hostnames into IP addresses via DNS. During network troubleshooting, if `ping 8.8.8.8` works but `nslookup google.com` fails, it pinpoints that the internet connection is active, but the DNS configuration is broken.

4. **Why should you be careful about sharing your MAC address, IP address, or `ipconfig /all` screenshots online? Relate your answer to data privacy.**
   Sharing details like your MAC address, internal IP topology, and local hostname exposes structural information about your system to potential attackers. Exposure of these identifiers compromises data privacy and can make network devices easier targets for unauthorized access, IP spoofing, or targeted local exploits.

---

### VII. Scoring Guide

| Criteria | Description | Points |
| :--- | :--- | :---: |
| **Completeness** | All tables (1-6) and required fields are filled out. | 25 |
| **Accuracy** | Recorded values match what the tools show and are consistent across Settings, CMD, and PowerShell; sample analysis, binary conversion, and OSI layers are correct. | 30 |
| **Network Design** | Diagram shows a star topology with PCs, switch, router, printer, and ISP; IP plan uses valid, non-duplicate addresses in `192.168.10.0/24`. | 15 |
| **Realization / Reflection** | Answers are thoughtful, based on the student's own results, and well written. | 20 |
| **Neatness & Timeliness** | Worksheet is legible/well-formatted and submitted on time. | 10 |
| **Total** | | **100** |
