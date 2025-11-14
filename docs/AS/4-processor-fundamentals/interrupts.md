# Interrupts in CPU Architecture

## Introduction

Interrupts are signals that temporarily halt the normal execution of a program to handle high-priority events. They enable efficient multitasking and responsive system operation.

## Purpose of Interrupts

- **Asynchronous Processing**: Handle events that occur unpredictably
- **Priority Management**: Allow urgent tasks to interrupt less critical ones
- **Resource Sharing**: Enable multiple devices to share CPU time
- **Real-time Response**: Provide immediate attention to time-sensitive events

## Possible Causes of Interrupts

### Hardware Interrupts

- **I/O Device Completion**: Printer finished printing, disk completed read/write
- **Timer Events**: System clock ticks, timeouts
- **Hardware Failures**: Power supply issues, memory errors
- **User Input**: Keyboard presses, mouse movements

### Software Interrupts

- **System Calls**: Program requests operating system services
- **Exceptions**: Division by zero, invalid memory access
- **Debugging**: Breakpoints in development
- **Page Faults**: Memory management events

## Applications of Interrupts

### Real-time Systems

- **Industrial Control**: Respond to sensor inputs immediately
- **Robotics**: Process feedback from motors and sensors
- **Medical Equipment**: Monitor patient vital signs continuously

### General Computing

- **User Interface**: Handle keyboard/mouse input
- **Networking**: Process incoming data packets
- **Multimedia**: Maintain audio/video synchronization
- **Background Tasks**: Disk I/O, printing operations

## Interrupt Service Routine (ISR)

### Definition

- Special function executed in response to an interrupt
- Also called Interrupt Handler

### Characteristics

- **High Priority**: Executes immediately when interrupt occurs
- **Short Duration**: Performs minimal processing
- **Context Saving**: Preserves current program state
- **Reentrant**: Can be interrupted by higher-priority interrupts

### Structure

1. **Save Context**: Store current register values
2. **Service Interrupt**: Perform required actions
3. **Restore Context**: Reload saved register values
4. **Return**: Resume interrupted program

## When Interrupts are Detected

### During Fetch-Execute Cycle

- **After Instruction Completion**: CPU checks for interrupts between instructions
- **At Cycle Boundaries**: Modern CPUs check at the end of each clock cycle
- **Maskable Interrupts**: Can be temporarily disabled
- **Non-Maskable Interrupts**: Cannot be ignored (power failure, hardware errors)

### Interrupt Timing

- **Synchronous**: Occur at predictable points (software interrupts)
- **Asynchronous**: Occur at unpredictable times (hardware interrupts)

## How Interrupts are Handled

### Interrupt Processing Steps

1. **Interrupt Detection**
   - CPU receives interrupt signal
   - Completes current instruction

2. **Interrupt Acknowledgment**
   - CPU saves current Program Counter
   - Disables further interrupts (optional)

3. **Context Saving**
   - Push registers onto stack
   - Save processor status

4. **ISR Execution**
   - Load ISR address from Interrupt Vector Table
   - Execute appropriate handler

5. **Context Restoration**
   - Pop registers from stack
   - Restore processor status

6. **Return from Interrupt**
   - Resume interrupted program
   - Re-enable interrupts

### Interrupt Vector Table

- **Purpose**: Maps interrupt types to ISR addresses
- **Location**: Fixed memory area
- **Entries**: Each interrupt has unique vector
- **Hardware Mapping**: Interrupt number determines table entry

### Priority Levels

- **Interrupt Priority**: Higher priority interrupts can preempt lower ones
- **Nested Interrupts**: Higher priority ISRs can interrupt lower priority ones
- **Priority Masking**: Temporarily disable lower priority interrupts

## Advanced Concepts

### Multiple Interrupt Handling

- **Interrupt Controller**: Manages multiple interrupt sources (e.g., 8259 PIC)
- **Spurious Interrupts**: False interrupt signals
- **Interrupt Latency**: Time from interrupt to ISR execution

### Modern Implementations

- **Advanced Programmable Interrupt Controllers (APIC)**
- **Message Signaled Interrupts (MSI)**: PCIe-based interrupts
- **Interrupt Affinity**: Assign interrupts to specific CPU cores

Interrupts are fundamental to modern computing, enabling responsive and efficient system operation.