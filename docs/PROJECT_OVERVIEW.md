# Veo Shared-Ride Scooter / E-Bike Reverse-Engineering & ESP32 Rebuild (Draft Beta)

**Status:** Research and design draft — not a validated repair manual or manufacturer specification.  
**Project date:**  
**Author:** TurnFlockOff / project owner

## Purpose
Organize the available research artifacts concerning Veo shared-rideshare scooter/e-bike electronics, display/control-module teardown concepts, wiring architecture, and an independent ESP32-based replacement-dashboard concept.

## Working hypothesis
The display/control assembly may combine a user interface, low-voltage power regulation, vehicle I/O and communications/telematics. A separate ESP32-based dashboard may be feasible if the actual vehicle-side interfaces are identified and electrically verified. Connector labels, wire colors, voltages, protocols and controller behavior in the available diagrams are not confirmed OEM facts.

## What was done
- Collected engineering illustrations and conceptual schematics.
- Mapped likely subsystems: battery/BMS, power conversion, motor controller, display PCB, main PCB, connector block, brake/throttle/sensor inputs, lighting, and possible GPS/LTE/Bluetooth telematics.
- Drafted an independent ESP32 dashboard architecture with display, buttons, indicators, and optional UART/sensor inputs.
- Created exploded-view and teardown-style illustrations to communicate a possible enclosure and board stack.

## What happened / current result
The material supports a coherent design hypothesis and a set of investigation aids. It does **not** establish that a scooter was successfully reverse engineered, that any pinout was confirmed, that a replacement dashboard was built or operated, or that vehicle communications were decoded. No verified bench-test logs, oscilloscope captures, firmware source, measured pinout table, or successful vehicle test record were located in the files searched for this publication.

## What I would change next
1. Separate direct photographs and measurements from AI-generated/conceptual illustrations.
2. Record each test with date, vehicle/model identifier (non-sensitive), instrument, probe point, measured value, and result.
3. Verify ground and voltage rails with a meter before connecting any controller or ESP32.
4. Identify signal levels and protocol passively first; use isolated interfaces and current limiting.
5. Build an independent, non-invasive bench prototype before considering vehicle integration.
6. Confirm legal ownership/authorization and avoid bypassing rental locks, payment controls, geofencing, fleet management, or safety interlocks.

## Safety and accuracy
All wiring diagrams and pinout descriptions are **illustrative only** unless explicitly marked as measured and verified. Do not apply power based solely on a drawing. Disconnect the battery before inspection and use appropriate isolation, fusing, and test equipment.

Dates are left blank where the source record did not establish a reliable creation or test date. Saved-file timestamps are not necessarily the date the underlying physical work occurred.
