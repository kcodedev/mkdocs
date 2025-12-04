# Monitoring and Control Systems


## Picture Examples

![Patient monitor](https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Dash_5000_Medical_monitor.jpg/330px-Dash_5000_Medical_monitor.jpg)

![Air conditioning system](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/ACFujitsu2.jpg/330px-ACFujitsu2.jpg)

## Pseudocode

### Monitoring System

```
WHILE true DO
    analogue_signal ← read_sensor()
    digital_signal ← ADC_convert(analogue_signal)
    IF digital_signal NOT in acceptable_range THEN
        send_warning_message()
        // Microprocessor observes without intervening
    END IF
END WHILE
```

### Control System

```
WHILE true DO
    analogue_signal ← read_sensor()
    digital_signal ← ADC_convert(analogue_signal)
    IF digital_signal NOT in acceptable_range THEN
        adjust_actuator()  // valves, motors, etc.
        // Actively control the system
    END IF
END WHILE
```

## Introduction

Monitoring and control systems use sensors and actuators to observe and manage processes. They are essential in automated environments for maintaining desired conditions.

## Monitoring vs Control

- **Monitoring Systems**: Observe and report on system states without intervening. They collect data for analysis or alerts.
- **Control Systems**: Actively adjust system parameters to achieve desired outcomes, using feedback to make decisions.

## Sensors

Sensors detect physical quantities and convert them into electrical signals. They provide input data for decision-making in systems

**Types and Uses**

  - **Light Sensors**: Photodiodes or phototransistors for light detection in cameras or automatic lighting systems.<br>
  - **Temperature Sensors**: Thermistors or thermocouples for measuring heat in HVAC systems or engines.<br>
  - **Pressure Sensors**: Piezoelectric or strain gauges for monitoring fluid pressure in industrial processes.<br>
  - **Infra-Red Sensors**: Detect IR radiation for motion detection or thermal imaging.<br>
  - **Sound Sensors**: Microphones for audio input or noise level monitoring.<br>

## Actuators

Actuators convert electrical signals into physical actions.

- **Examples**: Motors, solenoids, valves that open/close doors, adjust speeds, or control flows.
- **Role**: Execute commands from the control system to effect changes.

## Importance of Feedback

**Definition**: The process of using output measurements to adjust inputs, creating a closed-loop system.

**Benefits**:

- Improves accuracy and stability.
- Compensates for disturbances or errors.
- Enables automation and self-regulation.


## 📊❓Quiz 

For each of the following items, state whether it is a monitoring system or a control system.

- Digital watch
- MP3 player
- Weather station
- Thermostat
- air conditioner
- burglar alarm
- cruise control
- auto street light

| Device | Embedded system? | Monitoring system? | Control system? | Why |
|--------|------------------|---------------------|-----------------|-----|
| Digital watch | ✔️ | ❌ | ❌ | Displays time only |
| MP3 player | ✔️ | ❌ | ❌ | Plays stored audio |
| Weather station | ✔️ | ✔️ | ❌ | Uses sensors to collect data |
| Thermostat | ✔️ | ✔️ | ✔️ | Monitors temperature and controls heating |
| air conditioner | ✔️ | ✔️ | ✔️ | Monitors temperature and controls cooling |
| burglar alarm | ✔️ | ✔️ | ❌ | Monitors for intruders but does not control anything |
| cruise control | ✔️ | ✔️ | ✔️ | Monitors speed and controls engine |
| auto street light | ✔️ | ✔️ | ✔️ | Monitors light and controls street light |