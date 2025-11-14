# Data Transfer Buses

## Introduction

Buses are communication pathways that transfer data between different components of a computer system. The three main types of buses work together to enable efficient data movement.

## Address Bus

### Purpose

- Carries memory addresses from CPU to memory
- Specifies which memory location to access

### Characteristics

- **Unidirectional**: Only carries addresses from CPU to memory
- **Width**: Determines maximum addressable memory (e.g., 32-bit bus = 4GB address space)
- **Connected to**: CPU (MAR) to memory

### Operation

- CPU places address in Memory Address Register (MAR)
- Address is sent via address bus to memory
- Memory decodes address to select specific location

## Data Bus

### Purpose

- Transfers actual data between CPU and memory/peripherals
- Carries instructions and data in both directions

### Characteristics

- **Bidirectional**: Can transfer data in both directions
- **Width**: Determines amount of data transferred per cycle (8-bit, 16-bit, 32-bit, 64-bit)
- **Connected to**: CPU (MDR), memory, I/O devices

### Operation

- For reads: Data flows from memory to CPU's Memory Data Register (MDR)
- For writes: Data flows from MDR to memory location
- Width affects transfer speed and efficiency

## Control Bus

### Purpose

- Carries control signals that coordinate operations
- Manages timing and synchronization of data transfers

### Characteristics

- **Collection of Signals**: Multiple individual control lines
- **Direction**: Mostly unidirectional (CPU to peripherals), some bidirectional
- **Signals Include**: Read/Write, Memory Request, I/O Request, Interrupt Request

### Common Control Signals

- **Read/Write (R/W)**: Indicates read or write operation
- **Memory Request (MR)**: Signals memory access request
- **I/O Request (IOR)**: Signals input/output operation
- **Clock**: Synchronizes operations
- **Reset**: Initializes system
- **Interrupt**: Signals external events

## Bus Operation Example

### Memory Read Operation

1. CPU places address in MAR
2. Address sent via address bus to memory
3. Control bus signals "read" operation
4. Memory retrieves data from addressed location
5. Data sent via data bus to CPU's MDR

### Memory Write Operation

1. CPU places address in MAR and data in MDR
2. Address sent via address bus to memory
3. Data sent via data bus to memory
4. Control bus signals "write" operation
5. Memory stores data at addressed location

## Bus Width and Performance

- **Address Bus Width**: Affects maximum memory capacity
- **Data Bus Width**: Affects data transfer rate
- **Control Bus**: Affects system coordination efficiency

## Modern Developments

- **Multiple Buses**: Separate buses for different functions
- **Bus Arbitration**: Manages bus access in multi-processor systems
- **High-Speed Standards**: PCIe, USB for peripheral connections

Buses are fundamental to computer architecture, enabling communication between all system components.