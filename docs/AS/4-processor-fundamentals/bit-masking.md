# Bit Masking

## Introduction

Bit masking is a technique that uses bitwise logical operations to manipulate specific bits within a binary value. Masks are patterns that isolate or modify particular bits while leaving others unchanged.

## Creating Masks

### Bit Position Notation

- **Bit 0**: Rightmost (least significant) bit
- **Bit 7**: Leftmost (most significant) bit in a byte
- **Mask Value**: 2^bit_position

**Examples:**
```
Bit 0: 00000001 (1)
Bit 1: 00000010 (2)
Bit 2: 00000100 (4)
Bit 3: 00001000 (8)
```

### Multi-bit Masks

**Range of bits:**
```
Bits 0-3: 00001111 (15)
Bits 4-7: 11110000 (240)
Bits 1,3,5: 00101010 (42)
```

## Testing Bits

### Check if Bit is Set (1)

**Method:** AND with mask, check if result equals mask

```
; Test bit 3
LDA VALUE
AND #00001000  ; Mask for bit 3
JZ BIT_CLEAR   ; If zero, bit is clear
; Bit is set
```

**Alternative:** AND with mask, check if result ≠ 0

```
; Test bit 3 (shorter)
LDA VALUE
AND #00001000
JNZ BIT_SET    ; If not zero, bit is set
```

### Check if Bit is Clear (0)

**Method:** AND with mask, check if result equals 0

```
; Test if bit 3 is clear
LDA VALUE
AND #00001000
JNZ BIT_SET    ; If not zero, bit is set
; Bit is clear
```

## Setting Bits (Set to 1)

### Set Single Bit

**Method:** OR with mask

```
; Set bit 3
LDA VALUE
OR #00001000   ; Set bit 3
STA VALUE
```

### Set Multiple Bits

```
; Set bits 1, 3, 5
LDA VALUE
OR #00101010
STA VALUE
```

## Clearing Bits (Set to 0)

### Clear Single Bit

**Method:** AND with inverted mask

```
; Clear bit 3
LDA VALUE
AND #11110111  ; All 1s except bit 3
STA VALUE
```

**Inverted mask calculation:**
- Bit to clear: 3
- Mask: 00001000 (8)
- Inverted: 11110111 (247 = 255 - 8)

### Clear Multiple Bits

```
; Clear bits 0-3
LDA VALUE
AND #11110000  ; Keep upper 4 bits
STA VALUE
```

## Toggling Bits (Flip 0↔1)

### Toggle Single Bit

**Method:** XOR with mask

```
; Toggle bit 3
LDA VALUE
XOR #00001000
STA VALUE
```

### Toggle Multiple Bits

```
; Toggle bits 1, 3, 5
LDA VALUE
XOR #00101010
STA VALUE
```

## Advanced Masking Techniques

### Extract Bit Field

**Extract bits 4-7 from a byte:**
```
LDA VALUE
AND #11110000  ; Mask upper 4 bits
LSR #4         ; Shift to lower position
; Result in bits 0-3
```

### Insert Bit Field

**Insert value into bits 4-7:**
```
LDA VALUE
AND #00001111  ; Clear upper 4 bits
STA TEMP       ; Store result

LDA NEW_VALUE
AND #00001111  ; Mask to 4 bits
LSL #4         ; Shift to position 4-7
OR TEMP        ; Combine with cleared value
STA VALUE
```

### Conditional Bit Operations

**Set bit only if another bit is set:**
```
LDA VALUE
AND #00000100  ; Test bit 2
JZ SKIP        ; Skip if bit 2 clear
LDA VALUE
OR #00001000   ; Set bit 3
STA VALUE
SKIP:
```

## Practical Examples

### Device Control

**Control LED states (8 LEDs on port):**
```
; Turn on LED 3 (bit 3)
LDA PORTA
OR #00001000
STA PORTA

; Turn off LED 2 (bit 2)
LDA PORTA
AND #11111011
STA PORTA

; Toggle LED 1 (bit 1)
LDA PORTA
XOR #00000010
STA PORTA
```

### Status Checking

**Check multiple sensor states:**
```
LDA SENSOR_PORT
AND #00001111  ; Check lower 4 sensors
JZ ALL_CLEAR   ; All sensors clear
; Handle sensor activation
```

### Configuration Registers

**Set UART configuration:**
```
; Set 8-bit, no parity, 1 stop bit
LDA UART_CONFIG
AND #11110000  ; Clear lower 4 bits
OR #00000011   ; Set configuration
STA UART_CONFIG
```

## Mask Constants

### Define Named Masks

```
BIT0_MASK: 00000001
BIT1_MASK: 00000010
BIT2_MASK: 00000100
BIT3_MASK: 00001000
UPPER_NIBBLE: 11110000
LOWER_NIBBLE: 00001111
```

### Bit Position Macros

```
BIT_POS(n) = 1 << n
BIT_MASK(n) = ~(1 << n)  ; For clearing
```

## Common Patterns

### Flag Management

- **Set flags:** OR with flag mask
- **Clear flags:** AND with inverted flag mask
- **Toggle flags:** XOR with flag mask
- **Test flags:** AND with flag mask, compare result

### Data Packing

- **Pack multiple values:** Shift and OR operations
- **Unpack values:** Shift and mask operations
- **Bit fields:** Extract specific ranges of bits

### Hardware Interface

- **GPIO pins:** Individual bit control
- **Status registers:** Read/write specific flags
- **Control registers:** Set configuration bits

Bit masking provides precise control over individual bits, essential for efficient low-level programming and hardware interaction.