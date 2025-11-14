# 🌐 Understanding IP Addresses

An **IP address** (Internet Protocol address) is a unique label assigned to every device on a network. IP addresses let devices find and communicate with each other across the Internet and local networks.

---

## 🎯 1. IP Address Formats

### 🟦 IPv4 (32-bit)
- Written as **four** decimal numbers (0–255) separated by dots: 192.168.0.1
- Total possible addresses: ~4.3 billion

### 🟥 IPv6 (128-bit)
- Written as **eight** groups of four hexadecimal digits separated by colons:  
- 2001:0db8:85a3:0000:0000:8a2e:0370:7334
- Can **shrink** zeros with `::` (only once):  
- 2001:db8:85a3::8a2e:370:7334

- Total possible addresses: 3.4×10³⁸ (practically unlimited!)

---

## 🔍 2. Subnetting

- **Subnetting** divides a large network into smaller “sub-networks” (subnets).
- Uses a **subnet mask** (IPv4) or **prefix length** (IPv6) to define which bits are network vs host:  
- IPv4 example: `192.168.1.0/24` means the first 24 bits (`192.168.1`) are the network, last 8 bits are hosts (1–254).  
- IPv6 example: `2001:db8::/64` reserves the first 64 bits for network, last 64 for hosts.

**Benefits:**  
- Reduces broadcast traffic  
- Improves security and management  
- Enables logical grouping of devices  

---

## 🔗 3. IP ↔ Device Association

- A device gets an IP address via:  
1. **Static assignment** (manually configured)  
2. **Dynamic assignment** using **DHCP** (Dynamic Host Configuration Protocol)  
- The **NIC (Network Interface Card)** of each device uses its IP + MAC address to send and receive packets.  

---

## 🔒 4. Public vs Private IP Addresses

| Type           | Range / Example               | Visibility       | Security Implications                              |
|----------------|-------------------------------|------------------|----------------------------------------------------|
| **Public IP**  | Any routable IPv4/IPv6 address| Internet-wide    | Exposed to the Internet → must be firewalled and monitored 🔥 |
| **Private IP** | IPv4: 10.0.0.0/8, 192.168.0.0/16, 172.16.0.0/12<br>IPv6: fc00::/7 | Local networks only | Not routable on Internet → safer, but still require internal security 🔐 |

- **NAT** (Network Address Translation) lets multiple private-IP devices share a single public IP.

---

## 🔄 5. Static vs Dynamic IP Addresses

| Feature         | Static IP                               | Dynamic IP                              |
|-----------------|-----------------------------------------|-----------------------------------------|
| Assignment      | Manually set by network admin           | Automatically assigned by DHCP server   |
| Persistence     | Stays the same across reboots & time    | Can change on lease renewal or reboot   |
| Use Cases       | Servers, printers, cameras, IoT devices | PCs, laptops, phones, most client devices |
| Pros            | Reliable for remote access & DNS        | Easier to manage, fewer conflicts       |
| Cons            | Harder to maintain at scale             | Can complicate port-forwarding/setup    |

---

## Quiz: IPv4 vs IPv6

Test your knowledge! Are these IP addresses valid? (✅ = Valid, ❌ = Invalid)

*Note: Some exam boards (like Cambridge) accept hexadecimal notation in IPv4 if values are in the valid range (0-255).*

### IPv4 Examples
| IP Address    | Valid? |
|---------------|--------|
| 100.2.256.3   | ❌     |
| 1A.FF.1.4     | ✅*    |
| 190.0.1.1.2   | ❌     |

### IPv6 Examples
| IP Address                          | Valid? |
|-------------------------------------|--------|
| 21DA:D3:0:2F3B:2AA:FF:FE28:9C5A     | ✅     |
| 1200::AB00::2552:7777:1313          | ❌     |
| 0:0:0:0:0:FFFF:192.1.56.10          | ✅     |
| 1200:0000:AB00:1234:H000:2552:7777:1313 | ❌     |

## 🧠 Summary

- **IP addresses** uniquely identify devices on networks.  
- **IPv4 vs IPv6** differ in length and notation.  
- **Subnetting** groups devices and improves network efficiency.  
- Devices get IPs **statically** or via **DHCP**.  
- **Public IPs** face the Internet; **private IPs** stay inside local networks (secured by NAT/firewall).  
- **Static IPs** give consistency for servers; **dynamic IPs** simplify client network management.

Understanding IP addressing is key to designing, securing, and troubleshooting modern networks! 🚀🔧  

---

## 🖥️ Bonus: Check Your IPs

| Action                         | macOS / Linux Command(s)                        | Windows Command(s)                            |
|--------------------------------|-------------------------------------------------|-----------------------------------------------|
| **Check public IP (browser)**  | Open browser → `https://whatismyipaddress.com/`  | Open browser → `https://whatismyipaddress.com/` |
| **Check public IP (CLI)**      | ```curl ifconfig.me```               | ```curl ifconfig.me```       |
| **Check private IP**           | ```ifconfig``` or ```ip a``` or ```hostname -I``` | ```ipconfig```                      |


