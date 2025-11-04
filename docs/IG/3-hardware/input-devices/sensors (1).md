# Sensors 📡📟


- Sensors are input devices which measure a property of their environment (light, temperature etc.)
- In order to convert the data from the sensor into data which a computer can use, an ADC (analogue to digital converter) must be used.
- If a reading is used to alter the sensor in some way to affect the next reading taken, it is known as a feedback loop.
---

## Types of Sensors
|Name          |Descriptions                   |Image                 |
|:------------:|:----------------------:|----------------------|
|**Temperature🌡️**   | Measures temperature using signals, used to maintain temperature in control environments.     |![alt text](https://upload.wikimedia.org/wikipedia/commons/c/c2/Temperature_Sensor_%28TMP36%29.jpg)|
|**Sound🔊**         | Measures sound levels and converts them to, used in security systems or for detecting machinery noises.  | ![alt text](https://upload.wikimedia.org/wikipedia/commons/a/a8/Proximity_Meter_with_Sound_Speed_Calibration.jpg)
|**Light☀️**| Measures light levels, used in automatic light systems|![alt text](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSEcmyHky9vhoLXkf7yMbvzQgdgtuYAYF6b_w&s)|
|**Moisture💦**| Measures the water level in substances such as soil, similar to humidity sensors. Used in things like greenhouses.| ![alt text](https://upload.wikimedia.org/wikipedia/commons/d/d3/Temperature-humidity-sensor-module.jpg)|
|**Humidity💨**| Similar but different to moisture, measures the amount of water vapour in a gas| ![alt text](https://upload.wikimedia.org/wikipedia/commons/3/39/Capacitive_humidity_sensor_SHT.jpg)|
---
## Monitoring & Control Systems 💻

Sensors are used for both monitoring and control systems, which have some minor differences.
-  A monitoring system would simply read the data from the sensor and allow it to be viewed.
- A control system would read the data and make changes until the intended conditions are met.

### Flowchart
---
```mermaid
flowchart TD
    A[Start Monitoring/Control Process] --> B[Read Sensor Data]
    B --> C{Is data within acceptable range?}
    
    C -->|Yes| D[Continue Monitoring/Control]
    D --> B
    
    C -->|No| E[Monitoring System: Send Warning Message or Activate Alarm]
    E --> B
    
    C -->|No| F[Control System: Send Signals to Control Valves, Motors, etc.]
    F --> G[Actuators Affect the Process]
    G --> H[Output Influences Next Sensor Inputs]
    H --> B
```

### Examples
---
#### Monitoring
- The monitoring of a patient in a hospital
- The monitoring of intruders in a security system
- Checking the temperature levels of machinery
- Monitoring pollution levels

#### Control
- A system which turns on lights when it's night and turn's them off when it's day
- Controlling the conditions for a chemical process
- Controlling the temperature of a cooling/heating system   