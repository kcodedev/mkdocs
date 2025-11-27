# 🌐 Network Hardware: Connecting Devices

Network hardware enables communication between computers and devices. Key components include network interface cards, addresses, and routers that manage data flow across networks.

---

## Network Interface Card (NIC)

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c0/Eicon_Networks_E50409-002-8565.jpg/960px-Eicon_Networks_E50409-002-8565.jpg" alt="Network Interface Card">

Every device needs a NIC to connect to a network:

- **Purpose**: Enables communication between device and network
- **Types**: Wired (Ethernet) and wireless (Wi-Fi)
- **Function**: Converts data into network signals and vice versa

---

## MAC Address

Each NIC has a unique identifier called a MAC address:

- **Structure**: 48-bit hexadecimal number (e.g., 00:1A:2B:3C:4D:5E)
- **Components**: Manufacturer code + Serial number
- **Purpose**: Identifies devices on a local network
- **Assignment**: Set by manufacturer at production

### 🔍 Finding Your MAC Address

To find your device's MAC address using the command line:

**Windows:**

```cmd
ipconfig /all
```

Look for "Physical Address" under your network adapter.

**macOS/Linux:**

```bash
ifconfig
```

---

## IP Address

IP addresses identify devices on the internet:

- **Purpose**: Routing data to correct destination
- **Types**:
  - **IPv4**: 32-bit address (e.g., 192.168.1.1)
  - **IPv6**: 128-bit address for more devices
- **Assignment**: Static (fixed) or Dynamic (changes)
- **Allocation**: Managed by network router

### 🔍 Finding Your IP Address

To find your device's IP address using the command line:

**Windows:**

```cmd
ipconfig
```

Look for "IPv4 Address" under your network adapter.

**macOS/Linux:**

```bash
ifconfig
```

Look for "inet" followed by the IP address.

---

## Router

Routers direct network traffic:

- **Functions**:
  - Sends data to specific destinations
  - Connects local networks to the internet
  - Assigns IP addresses to devices
  - Manages network security

**Router Capabilities:**

- **IP Assignment**: DHCP server functionality
- **Network Connection**: Gateway between LAN and internet
- **Traffic Management**: Routes packets efficiently

---

## Key Points

- NIC enables network connection ✅
- MAC address uniquely identifies hardware ✅
- IP address enables internet communication ✅
- Router manages network traffic ✅
