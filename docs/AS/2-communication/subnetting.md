# Subnetting in a Network

## What is Subnetting?

**Subnetting** is the process of dividing a larger network into smaller, more efficient segments called **subnets**. It allows for better IP address management, improved security, and reduced network congestion.

---

## Why Subnet?

- 🔄 **Efficient IP Usage**: Prevents wasting IP addresses.
- 🔐 **Improved Security**: Isolates departments or systems.
- 🚀 **Better Performance**: Reduces broadcast domain size.
- 🧩 **Easier Troubleshooting**: Smaller segments are easier to manage.

---

## Key Concepts

- **Network ID**: Identifies the subnet.
- **Host ID**: Identifies a device within the subnet.
- **Subnet Mask**: Defines how many bits are used for the network vs. the host.

---

## Understanding CIDR and Binary

In CIDR notation, an IP address like `192.168.1.0/26` means:

- The **first 26 bits** are used for the **network ID**
- The **remaining 6 bits** are used for **host addresses**


---

## Subnetting Example

Suppose a company is assigned a public Class C block:

The company has **4 departments**, each needing around **50 hosts**.  
We can divide the `/24` block into **4 subnets** of `/26`, like this:

| Subnet | Network Address    | Usable Host Range       | Broadcast Address   | Department  |
|--------|--------------------|--------------------------|---------------------|-------------|
| /26 #1 | `203.0.113.0/26`   | `203.0.113.1 – .62`      | `203.0.113.63`      | Finance     |
| /26 #2 | `203.0.113.64/26`  | `203.0.113.65 – .126`    | `203.0.113.127`     | Support     |
| /26 #3 | `203.0.113.128/26` | `203.0.113.129 – .190`   | `203.0.113.191`     | Engineering |
| /26 #4 | `203.0.113.192/26` | `203.0.113.193 – .254`   | `203.0.113.255`     | Sales       |

Each subnet supports **62 usable host addresses** — perfect for the ~50 devices per department.

---

## How the Router Uses Subnet Bits

You're borrowing **2 bits** from the host portion of the address:

- `00` → Finance
- `01` → Support
- `10` → Engineering
- `11` → Sales

A router can read these subnet ID bits and route traffic appropriately.

This is how **CIDR** (Classless Inter-Domain Routing) enables **flexible, efficient subnetting**, even outside the rigid old Class A/B/C system.

---

## Summary

- CIDR lets you divide IP blocks precisely, like splitting a `/24` into four `/26`s.
- Subnetting supports better network design, security, and scalability.
- Routers use subnet IDs to direct packets within your internal network.

---
