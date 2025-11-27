# Types of Programmable ROM

![16Mbit EPROM ST Microelectronics M27C160](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/16Mbit_EPROM_ST_Microelectronics_M27C160_%281%29.jpg/960px-16Mbit_EPROM_ST_Microelectronics_M27C160_%281%29.jpg)


## Introduction

Programmable Read-Only Memory (PROM) and its variants allow data to be written once or multiple times, providing flexibility in storing permanent data.

## Programmable ROM (PROM)

**Definition**: Blank ROM chips that can be programmed once by the user using a special device.

**Characteristics**:

  - One-time programmable.
  - Fuses or links are blown to set bits.
  - Non-volatile.

**Use**: Custom firmware or data that doesn't need changes.

## Erasable Programmable ROM (EPROM)

**Definition**: Can be erased and reprogrammed multiple times using ultraviolet (UV) light.

**Characteristics**:

  - Erasure requires exposure to UV light through a quartz window.
  - Reprogrammable, but erasure is not selective (entire chip).
  - Non-volatile when programmed.

- **Use**: Development and prototyping where code needs updates.

## Electrically Erasable Programmable ROM (EEPROM)

**Definition**: Can be erased and reprogrammed electrically, byte by byte.

**Characteristics**:

  - No need for UV light; uses electrical signals.
  - Selective erasure and writing.
  - Slower write times than RAM.
  - Non-volatile.

**Use**: BIOS updates, configuration storage, and devices requiring frequent small changes.

## Key Differences

| Aspect | PROM | EPROM | EEPROM |
|--------|------|-------|---------|
| Programmability | Once | Multiple with UV | Multiple electrically |
| Erasure Method | None | UV light | Electrical |
| Erasure details | Cannot be erased | Needs to be removed to be erased | Can be erased in situ |
| Speed and Cost | Fast, cheap | Moderate | Slower, more expensive |
| Usage | Custom firmware or data that doesn't need changes | Development and prototyping where code needs updates | BIOS updates, configuration storage, and devices requiring frequent small changes |
