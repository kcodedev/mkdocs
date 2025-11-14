# Types of Programmable ROM

## Introduction

Programmable Read-Only Memory (PROM) and its variants allow data to be written once or multiple times, providing flexibility in storing permanent data.

## Programmable ROM (PROM)

- **Definition**: Blank ROM chips that can be programmed once by the user using a special device.
- **Characteristics**:
  - One-time programmable.
  - Fuses or links are blown to set bits.
  - Non-volatile.
- **Use**: Custom firmware or data that doesn't need changes.

## Erasable Programmable ROM (EPROM)

- **Definition**: Can be erased and reprogrammed multiple times using ultraviolet (UV) light.
- **Characteristics**:
  - Erasure requires exposure to UV light through a quartz window.
  - Reprogrammable, but erasure is not selective (entire chip).
  - Non-volatile when programmed.
- **Use**: Development and prototyping where code needs updates.

## Electrically Erasable Programmable ROM (EEPROM)

- **Definition**: Can be erased and reprogrammed electrically, byte by byte.
- **Characteristics**:
  - No need for UV light; uses electrical signals.
  - Selective erasure and writing.
  - Slower write times than RAM.
  - Non-volatile.
- **Use**: BIOS updates, configuration storage, and devices requiring frequent small changes.

## Key Differences

- **Programmability**: PROM once; EPROM multiple with UV; EEPROM multiple electrically.
- **Erasure Method**: PROM none; EPROM UV; EEPROM electrical.
- **Flexibility**: EEPROM offers the most flexibility for updates.
- **Speed and Cost**: EEPROM is slower and more expensive than EPROM.

## Applications

- PROM: Secure, one-time use in embedded systems.
- EPROM: Historical use in early computing for firmware.
- EEPROM: Modern devices like USB drives, smart cards, and microcontrollers for updatable storage.