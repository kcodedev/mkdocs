# 🧩 How Applications Run on a Computer

To run your favourite apps, a chain of software and hardware must work together. Here's how it flows:

---

## 🧑‍💻 Applications Run on the Operating System

- Apps (like browsers, games, editors) depend on the **OS** to interact with hardware
- The OS provides the environment and system resources for them to run

---

## ⚙️ The Operating System Runs on Firmware

- The OS is launched by **firmware** during startup
- The **bootloader**, a type of firmware, begins the boot process and loads the OS into memory
- Loads the OS into which memory❓

---

## 🔩 Firmware Runs on Hardware

- Firmware is stored in **ROM** or **flash memory** on the hardware
- It's the first thing that runs when a device powers on

---

## 🧵 The Chain in Action

```text
[ Hardware ] 🔁 [ Firmware / Bootloader ] 🔁 [ Operating System ] 🔁 [ Applications ]
```

Each layer relies on the one below it, forming a stack that allows high-level apps to function smoothly on physical devices.

📝 Summary:

Apps need an OS to run ✅

The OS needs firmware to load ✅

Firmware relies on hardware to exist ✅

Everything is connected — and it all starts with the hardware! 🔌
