# Network Address Translation (NAT)

## What is NAT?

Network Address Translation (NAT) is a technique used by routers to translate private (local) IP addresses within a home or office network into a single public IP address for communication over the internet.

This allows multiple devices on a local network to share one public IP address.

---

## Why is NAT Important?

- **Conserves public IP addresses:** IPv4 addresses are limited, and NAT helps reduce the number of public IPs needed.
- **Improves security:** Devices on a private network are hidden from the outside internet, making it harder for external attackers to access them directly.
- **Enables multiple devices:** Allows many devices (computers, phones, IoT devices) to connect to the internet using a single public IP.

---

## How Does NAT Work?

1. Devices inside a local network have **private IP addresses** (e.g., `192.168.1.x`).
2. When a device sends data to the internet, the router **changes the source IP address** from the private IP to the router’s public IP.
3. The router keeps track of outgoing connections and uses **port numbers** to map responses back to the correct device inside the local network.
4. Incoming data from the internet is translated back to the appropriate private IP based on these mappings.

---

## Types of NAT

### 1. Static NAT

- Maps one private IP address to one public IP address.
- Used when a device needs to be accessible from the internet (e.g., a web server).

### 2. Dynamic NAT

- Maps a private IP address to any available public IP address from a pool.
- Less common due to limited public IPs.

### 3. PAT (Port Address Translation) — Also called NAT Overload

- Most common type in home routers.
- Maps multiple private IP addresses to a single public IP address by using different port numbers.
- Enables many devices to share one public IP.

---

## Example

| Private Network                 | Public Internet          |
| ------------------------------|-------------------------|
| Device 1: 192.168.1.10        |                         |
| Device 2: 192.168.1.11        |                         |
| Router’s Private IP: 192.168.1.1 | Router’s Public IP: 203.0.113.5 |

- Device 1 sends a request to a website.
- Router replaces `192.168.1.10` with `203.0.113.5` in the outgoing packets.
- Router assigns a unique port number to this connection.
- When the website responds, the router uses the port number to forward data back to Device 1.

---

## Why You Should Care About NAT

- Helps you understand how your home or office internet works.
- Explains why some services require **port forwarding** to be accessible externally.
- Clarifies concepts like **private IP**, **public IP**, and **firewalls**.

---

## See Also

- [Private vs Public IP Addresses](ip-addresses.md)
- [How Routers Work](https://en.wikipedia.org/wiki/Network_address_translation)
- [Port Forwarding](https://en.wikipedia.org/wiki/Port_forwarding)

