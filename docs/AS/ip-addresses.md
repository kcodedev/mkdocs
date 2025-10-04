# Public and Private IP Addresses

## What is an IP Address?

An IP address (Internet Protocol address) is a unique identifier for a device on a network. It allows devices to communicate with each other over the internet or local networks.

---

## Public IP Address

- A **public IP address** is assigned by your Internet Service Provider (ISP).
- It is **unique across the entire internet**.
- Used to identify your network to the outside world.
- Example: `203.0.113.25`

### Use Cases:
- Hosting a website or server.
- Accessing services over the internet.

---

## Private IP Address

- A **private IP address** is used **within a local network**.
- It is **not routable on the internet**.
- Assigned by your router to devices on your network.
- Examples: `192.168.1.10`, `10.0.0.5`, `172.16.0.1`

### Use Cases:
- Home networks, office LANs.
- Connecting phones, laptops, printers locally.

---

## Key Differences

| Feature         | Public IP              | Private IP              |
|-----------------|------------------------|--------------------------|
| Visibility      | Global (Internet)      | Local (LAN)              |
| Uniqueness      | Must be unique         | Can be reused in networks|
| Assigned by     | ISP                    | Router (via DHCP)        |
| Accessibility   | Accessible from Internet| Only inside local network|

---

## Why It Matters

- **Security**: Private IPs help isolate local traffic from the public internet.
- **Scalability**: [NAT](nat.md) (Network Address Translation) allows multiple devices to share a single public IP.
- **Cost**: ISPs may charge for static public IPs; private IPs are free.

---

## Bonus: Check Your IPs

Check public IP

- via browser: https://whatismyipaddress.com/
- via CLI: `curl ifconfig.me`

Check private IP:

- On Linux/macOS: `hostname -I` or `ip a` or `ifconfig`
- On Windows: `ipconfig`


