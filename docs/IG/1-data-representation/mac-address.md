---
### 📝 Finding Your Mac Address

A **MAC address** (Media Access Control address) is a unique identifier assigned to a network interface controller (NIC) for communication on the physical network segment. Think of it as your computer's personal "serial number" for networking. You might need it for various reasons, like connecting to a secure network, troubleshooting, or setting up a router. Here’s how you can find it on different operating systems.

### 💻 On Windows

1.  Press the **Windows key** + **R** to open the Run dialog.
2.  Type `cmd` and press **Enter** to open the Command Prompt.
3.  In the Command Prompt window, type `ipconfig /all` and press **Enter**.
4.  Look for your active network adapter (e.g., Wireless LAN adapter Wi-Fi or Ethernet adapter).
5.  The MAC address is listed next to **Physical Address**.

---

### 🐧 On Linux or 🍎 On macOS

1.  Open the **Terminal**.
2.  Type `ifconfig` and press **Enter**.
3.  Find your network adapter (e.g., `eth0` for Ethernet or `wlan0` for Wi-Fi).
4.  The MAC address is listed next to **ether** or **HWaddr**.

Alternatively, you can use the `ip` command:
1.  Open the **Terminal**.
2.  Type `ip a` and press **Enter**.
3.  Look for your network adapter and find the MAC address listed next to **link/ether**.

---

### 📱 On Mobile Devices

* **iOS (iPhone/iPad):** Go to **Settings** > **General** > **About**. The Wi-Fi address is your MAC address.
* **Android:** Go to **Settings** > **About phone** > **Status**. The Wi-Fi MAC address is listed here. (The exact path might vary slightly depending on your Android version and device manufacturer.)
