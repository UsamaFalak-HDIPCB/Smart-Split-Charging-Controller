# Smart-Split-Charging-Controller
Self-Employed / Freelance


<img width="1017" height="752" alt="Image" src="https://github.com/user-attachments/assets/f8ebe7f2-c1b5-4a96-99f1-836e1919e330" />


## 
ESP32-S3 based dual-battery split-charging controller with battery telemetry, relay-controlled DC-DC chargers, cooling management, and USB/UART connectivity.

# Smart Split Charging Controller

Smart Split Charging Controller is an ESP32-S3 based power-management and telemetry system designed for dual-battery vehicle installations.
The system automates the charging of an auxiliary battery bank from a vehicle alternator while protecting the primary starter battery from excessive loading or discharge. It combines battery monitoring, relay-controlled charger management, cooling control, telemetry collection, and communication interfaces into a single embedded platform.

The hardware integrates an ESP32-S3 microcontroller, isolated battery sensing circuitry, multi-UART expansion, relay outputs, USB connectivity, status indication, and a protected automotive power architecture.



## Charging Workflow

### Engine Start Detection

When the main battery voltage rises above 14.1 V, the system assumes the alternator is actively charging and starts a 20-minute stabilization timer.

### Primary Battery Priority

During the timer period, charging of the auxiliary battery remains disabled to allow the starter battery to recover first.

### Bulk Charging Mode

After the timer expires:

- Charger Relay 1 turns ON
- Charger Relay 2 turns ON

This enables maximum charging current to the auxiliary battery bank.

Thirty seconds later:

- Cooling Fan Relay turns ON

to assist thermal management of the charging system.

### Charge Tapering

When the auxiliary battery reaches 14.0 V:

- Charger Relay 1 turns OFF
- Charger Relay 2 remains ON
- Cooling Fan remains ON

This reduces charging current as the battery approaches full charge.

### Engine-Off Protection

If the main battery voltage drops below 13.0 V:

- All relays immediately turn OFF
- Charging stops
- Cooling fan stops
- Timers are reset

This prevents auxiliary loads from discharging the vehicle's starter battery.



## Hardware Features

- ESP32-S3 microcontroller
- 3 independent relay outputs
- Dual 16-bit voltage-monitoring channels
- Isolated battery sensing interfaces
- MAX14830 quad-UART expansion
- USB Type-C programming interface
- USB-to-UART bridge
- Automotive-grade input protection
- 12V to 5V DC/DC conversion
- 5V to 3.3V regulation
- Relay status indication using bi-color LEDs
- GPIO expansion headers
- Auxiliary communication interfaces



## Applications

- Commercial trucks
- Recreational vehicles (RV)
- Camper vans
- Fleet management systems
- Auxiliary battery systems
- DC-DC charger automation
- Vehicle telemetry platforms
- Mobile power systems



## Functionality

The controller continuously monitors:

- Main vehicle battery voltage
- Auxiliary battery voltage

Based on configurable voltage thresholds and timing rules, the system automatically manages charging and cooling devices.

Main functions include:

- Starter battery protection
- Auxiliary battery charging control
- Automatic charger sequencing
- Cooling fan control
- Voltage telemetry
- Remote monitoring capability
- Serial communication expansion
- USB debugging and firmware updates


<img width="857" height="575" alt="Image" src="https://github.com/user-attachments/assets/b48956cd-ed89-4c80-934f-7188b9375273" />
