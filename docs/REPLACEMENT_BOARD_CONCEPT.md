# ESP32-S3 replacement-board concept

## Design intent

Create a drop-in-style replacement for the original middle electronics board, reusing the enclosure and connector positions if measurements show that this is mechanically and electrically feasible. The ESP32-S3 would host custom firmware and communicate with a companion phone app over Bluetooth LE and/or Wi-Fi.

This is a proposal, not a finished schematic or PCB.

## Proposed functional blocks

1. **Input power protection:** fuse, reverse-polarity protection, transient suppression, filtering, and a DC/DC stage selected for the confirmed battery maximum voltage.
2. **ESP32-S3 module:** module-based design for easier RF/layout implementation and firmware development.
3. **Logic supply:** regulated 3.3 V rail sized for ESP32 and peripherals.
4. **USB programming/debug:** USB-C or a documented programming header with ESD protection.
5. **Vehicle interface connectors:** matching connector family and physical orientation only after exact part numbers and dimensions are identified.
6. **Protected input conditioning:** brake-state and other digital inputs through appropriate dividers, buffers, or isolation.
7. **Analog input conditioning:** throttle/sensor monitoring only after voltage range and safety requirements are measured. Initial firmware should not command propulsion.
8. **Communications:** UART first if the bus is confirmed; CAN transceiver only if the vehicle bus is verified as CAN. Include test pads and selectable interface options.
9. **Low-side/high-side drivers:** speaker, LED, and light outputs only after load voltage/current/polarity are characterized.
10. **Status and test access:** power, fault, BLE/Wi-Fi, UART activity LEDs; labeled test pads and programming access.

## Power design note

The battery label in the available photo reads 46.8 V / 15 Ah / 702 Wh, but the smaller series/parallel text is unclear and potentially inconsistent. Do not finalize the DC/DC input rating until the battery's maximum voltage is confirmed. The design should include suitable margin above the confirmed maximum voltage and transients, with input protection and thermal design.

A 5 V rail is a convenient intermediate rail for some ESP32 development boards, but the actual module supply is 3.3 V. The design must follow the selected module's datasheet and hardware design guidelines. Do not connect raw traction-battery voltage to the ESP32.

## Mechanical design

The earlier concept illustration included placeholder dimensions of 107 × 38 mm and 1.6 mm thickness. These values are not measured. Replace them with:
- PCB outline and corner radii
- Mounting-hole center coordinates and diameters
- Connector centerlines, height, and mating direction
- Maximum component height on both sides
- Enclosure internal keep-out volume
- Display stack-up and gasket compression
- Screw lengths, standoff heights, and cable bend radii

## CAD deliverables required for a real design

- KiCad schematic (.kicad_sch)
- KiCad PCB (.kicad_pcb)
- Custom symbols and footprints where required
- Component STEP models
- Mechanical enclosure CAD (STEP or native CAD)
- Assembly drawing with measured dimensions
- BOM with manufacturer part numbers
- Gerber and drill files after design review
- Electrical test plan and firmware source

## Revision strategy

- **Rev A — measurement / adapter prototype:** breakout connectors, protected monitoring inputs, USB, ESP32 module, and power supply. No propulsion control.
- **Rev B — verified interface board:** add only those outputs and protocols that have been measured and tested.
- **Rev C — enclosure-fit prototype:** match measured mounting and connector geometry; validate thermals, vibration, water ingress, and serviceability.

## Status

Concept only. No verified schematic, layout, fabrication files, or fit-checked CAD assembly are included at this stage.
