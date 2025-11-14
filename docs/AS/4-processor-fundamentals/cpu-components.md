# CPU Components: ALU, CU, Clock, and IAS

## Introduction

The Central Processing Unit (CPU) consists of several key components that work together to execute instructions and process data.

## Arithmetic and Logic Unit (ALU)

### Purpose

- Performs all arithmetic and logical operations
- Executes mathematical calculations and comparisons

### Functions

- **Arithmetic Operations**: Addition, subtraction, multiplication, division
- **Logical Operations**: AND, OR, NOT, XOR, comparisons
- **Bit Operations**: Shifts, rotates, bit manipulation

### Operation

- Receives data from registers
- Performs operations based on control signals
- Outputs results to registers or flags to status register

## Control Unit (CU)

### Purpose

- Coordinates and controls all CPU operations
- Manages the execution of instructions

### Functions

- **Instruction Decoding**: Interprets opcodes and operands
- **Sequencing**: Ensures instructions execute in correct order
- **Control Signals**: Generates signals to activate appropriate components
- **Fetch-Decode-Execute**: Manages the instruction cycle

### Components

- Instruction decoder
- Control logic circuits
- Timing circuits

## System Clock

### Purpose

- Provides timing signals for synchronization
- Coordinates all CPU operations

### Characteristics

- **Clock Speed**: Measured in Hz (cycles per second)
- **Clock Cycle**: Time for one complete cycle
- **Clock Signal**: Square wave alternating between high and low

### Role

- Synchronizes register transfers
- Determines maximum processing speed
- Affects overall system performance

## Immediate Access Store (IAS)

### Purpose

- Provides fast, temporary storage for CPU operations
- Also known as primary memory or RAM

### Characteristics

- **Volatility**: Loses data when power is removed
- **Speed**: Much faster than secondary storage
- **Capacity**: Limited compared to secondary storage

### Functions

- Stores currently executing program instructions
- Holds data being processed
- Acts as working memory for the CPU

## Interconnection

- **Buses**: Connect components for data transfer
- **Registers**: Provide intermediate storage
- **Control Signals**: Coordinate component activities

## Performance Impact

- ALU speed affects calculation performance
- CU efficiency determines instruction throughput
- Clock speed limits maximum operations per second
- IAS speed impacts memory access bottlenecks

These components work in harmony to execute the fetch-decode-execute cycle and process instructions efficiently.