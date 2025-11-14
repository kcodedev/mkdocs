# Device Control with Bit Manipulation

## Introduction

Bit manipulation is crucial for interfacing with hardware devices in embedded systems and computer peripherals. Devices often use individual bits or groups of bits to represent status, control signals, and configuration settings.

## Hardware Registers

### Status Registers

Status registers provide information about device state using individual bits.

**Example: Serial Port Status Register**
```
Bit 7: Data Ready (1 = data available)
Bit 6: Transmitter Empty (1 = ready to send)
Bit 5: Overrun Error (1 = data lost)
Bit 4: Framing Error (1 = invalid stop bit)
Bit 3: Parity Error (1 = parity mismatch)
Bit 2: Transmitter Ready (1 = can accept data)
Bit 1: Receiver Ready (1 = data received)
Bit 0: Interrupt Pending (1 = interrupt occurred)
```

**Reading Status:**
```
LDA SERIAL_STATUS
AND #10000000      ; Test Data Ready bit
JZ NO_DATA         ; No data available
; Process received data
```

### Control Registers

Control registers accept commands through specific bit patterns.

**Example: Motor Control Register**
```
Bit 7-6: Speed (00=slow, 01=medium, 10=fast, 11=max)
Bit 5: Direction (0=clockwise, 1=counter-clockwise)
Bit 4: Enable (1=motor on, 0=motor off)
Bit 3-0: Reserved (set to 0)
```

**Setting Control:**
```
; Set motor to fast, counter-clockwise, enabled
LDA #10110000      ; Speed=fast, Dir=CCW, Enable=on
STA MOTOR_CONTROL
```

## Input/Output Ports

### Digital I/O Pins

Microcontrollers use ports with 8-32 pins, each controllable individually.

**Example: LED Control on Port A**
```
; Turn on LEDs connected to bits 0, 2, 4
LDA PORTA
OR #00010101       ; Set bits 0, 2, 4
STA PORTA
```

**Example: Button Reading**
```
; Check if button on bit 3 is pressed (active low)
LDA PORTB
AND #00001000      ; Mask bit 3
JZ BUTTON_PRESSED  ; Active low: 0 = pressed
```

### Analog-to-Digital Conversion

ADC results often stored in registers with specific bit layouts.

**Example: 10-bit ADC Result**
```
Bits 9-0: ADC value (0-1023)
Bits 15-10: Reserved
```

**Reading ADC:**
```
LDA ADC_HIGH       ; Get bits 9-2
STA TEMP
LDA ADC_LOW        ; Get bits 1-0
AND #00000011      ; Mask lower 2 bits
OR TEMP            ; Combine with high bits
; Result in accumulator
```

## Interrupt Control

### Interrupt Enable Registers

Enable or disable specific interrupt sources.

**Example: Timer Interrupt Control**
```
; Enable timer 1 overflow interrupt
LDA TIMSK1
OR #00000001       ; Set TOIE1 bit
STA TIMSK1
```

### Interrupt Flag Registers

Check and clear interrupt flags.

**Example: Clear External Interrupt Flag**
```
; Clear INT0 flag
LDA EIFR
OR #00000001       ; Writing 1 clears the flag
STA EIFR
```

## Communication Protocols

### Serial Communication

UART registers use bit manipulation for control and status.

**Example: UART Configuration**
```
; Set 8-bit, no parity, 1 stop bit
LDA UCSR0C
AND #11000011      ; Clear configuration bits
OR #00000110       ; Set 8-bit mode
STA UCSR0C
```

### SPI/I2C Control

Bit-banging protocols require precise timing control.

**Example: SPI Bit Transfer**
```
; Send bit to MOSI pin
LDA DATA_BYTE
AND #10000000      ; Get MSB
JZ SEND_LOW
; Set MOSI high
LDA PORTB
OR #00001000       ; MOSI bit
JMP SEND_DONE
SEND_LOW:
LDA PORTB
AND #11110111      ; Clear MOSI bit
SEND_DONE:
STA PORTB
; Clock pulse
OR #00000100       ; Set SCK
STA PORTB
AND #11111011      ; Clear SCK
STA PORTB
```

## Sensor Interfaces

### Digital Sensors

Many sensors provide status through digital pins or registers.

**Example: Temperature Sensor**
```
; Read temperature ready flag
LDA TEMP_STATUS
AND #00000001      ; Check ready bit
JZ NOT_READY
; Read temperature value
LDA TEMP_HIGH
STA TEMP_VALUE
```

### Analog Sensors with Thresholds

Use bit manipulation for threshold comparison.

**Example: Light Sensor with Threshold**
```
LDA LIGHT_SENSOR
CMP THRESHOLD
JZ EQUAL
JC BELOW_THRESHOLD
; Above threshold
LDA STATUS_REG
OR #00000100       ; Set "bright" flag
JMP DONE
BELOW_THRESHOLD:
LDA STATUS_REG
AND #11111011      ; Clear "bright" flag
DONE:
STA STATUS_REG
```

## Device Configuration

### Mode Selection

Devices often have multiple operating modes selected by bit patterns.

**Example: LCD Display Mode**
```
; Set 4-bit mode, 2-line display
LDA LCD_CONTROL
OR #00101000       ; Function set: 4-bit, 2-line
STA LCD_CONTROL
```

### Feature Enable/Disable

Enable or disable device features through control bits.

**Example: Enable Watchdog Timer**
```
LDA WDTCSR
OR #00001000       ; Set WDCE bit to enable changes
STA WDTCSR
; Now set watchdog timeout
AND #11111000      ; Clear prescaler bits
OR #00000111       ; Set maximum timeout
STA WDTCSR
```

## Error Handling

### Error Flag Checking

Monitor device error conditions.

**Example: Check for I2C Bus Errors**
```
LDA TWSR
AND #11111000      ; Mask status bits
CMP #0x00          ; Check for start condition
JZ START_SUCCESS
; Handle start condition error
```

### Recovery Operations

Use bit manipulation to reset error conditions.

**Example: Clear UART Error Flags**
```
; Clear framing, overrun, parity errors
LDA UCSR0A
OR #00010100       ; Set error clear bits
STA UCSR0A
```

## Real-time Control Systems

### PID Controller Implementation

Bit manipulation for control algorithm flags.

**Example: Motor Speed Control**
```
; Check error sign
LDA ERROR
JZ ZERO_ERROR
JC NEGATIVE_ERROR
; Positive error - increase speed
LDA MOTOR_CONTROL
OR #00010000       ; Increase speed bit
JMP UPDATE_MOTOR
NEGATIVE_ERROR:
LDA MOTOR_CONTROL
AND #11101111      ; Decrease speed bit
UPDATE_MOTOR:
STA MOTOR_CONTROL
ZERO_ERROR:
```

## Best Practices

### Atomic Operations

Ensure bit operations don't interfere with interrupts.

**Example: Interrupt-safe bit set**
```
CLI               ; Disable interrupts
LDA PORTA
OR #00000001      ; Set bit
STA PORTA
SEI               ; Enable interrupts
```

### Bit Field Definitions

Define constants for bit positions.

```
#define LED1_BIT 0
#define LED2_BIT 1
#define BUTTON_BIT 3
#define MOTOR_EN_BIT 4
```

### Error Checking

Always verify bit operations succeeded.

**Example: Verify write operation**
```
LDA DESIRED_VALUE
STA CONTROL_REG
LDA CONTROL_REG    ; Read back
CMP DESIRED_VALUE
JZ WRITE_SUCCESS
; Handle write failure
```

Bit manipulation enables precise control and monitoring of hardware devices, forming the foundation of embedded systems programming.