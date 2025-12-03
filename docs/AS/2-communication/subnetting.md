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
- **Broadcast Address**: Used to send data to all devices on the subnet simultaneously.

---

## Subnetting Example

A company has **4 departments**, each needing around **50 hosts**.  Suppose the company is assigned a public Class C block. A Class C network block uses:

- 24 bits for the network ID
- 8 bits for the host ID, 

This provides 256 total IP addresses. 

Before subnetting, all departments would share the same broadcast domain, potentially leading to network congestion and security risks. 

After subnetting into four subnets, each department gets an isolated segment with 64 addresses (62 usable hosts), improving efficiency, security, and manageability.

## Subnet Assignments

To subnet the network into **4 subnets**, we borrow **2 bits** from the host portion of the address:

- `00` → Finance
- `01` → Support
- `10` → Engineering
- `11` → Sales

---

## Subnet Mask Calculation
To calculate the subnet mask `255.255.255.192`:

1. Start with the default Class C mask: `255.255.255.0` (binary: `11111111.11111111.11111111.00000000`).
2. Borrow **2 bits** from the host portion: `11111111.11111111.11111111.11000000`.
3. Convert back to decimal: `255.255.255.192`.


**Subnet Bit Examples:**

| Subnet Bits | Binary (last octet) | Network Address | Department |
|-------------|---------------------|-----------------|------------|
| `00` | `00000000` | `203.0.113.0` | Finance |
| `01` | `01000000` | `203.0.113.64` | Support |
| `10` | `10000000` | `203.0.113.128` | Engineering |
| `11` | `11000000` | `203.0.113.192` | Sales |

---

## Subnet Table

| Subnet | Network Address    | Subnet Mask       | Usable Host Range       | Broadcast Address   | Department  |
|--------|--------------------|-------------------|--------------------------|---------------------|-------------|
| Subnet 1 | `203.0.113.0`   | `255.255.255.192` | `203.0.113.1 – .62`      | `203.0.113.63`      | Finance     |
| Subnet 2 | `203.0.113.64`  | `255.255.255.192` | `203.0.113.65 – .126`    | `203.0.113.127`     | Support     |
| Subnet 3 | `203.0.113.128` | `255.255.255.192` | `203.0.113.129 – .190`   | `203.0.113.191`     | Engineering |
| Subnet 4 | `203.0.113.192` | `255.255.255.192` | `203.0.113.193 – .254`   | `203.0.113.255`     | Sales       |

Each subnet supports **62 usable host addresses** — perfect for the ~50 devices per department.

---