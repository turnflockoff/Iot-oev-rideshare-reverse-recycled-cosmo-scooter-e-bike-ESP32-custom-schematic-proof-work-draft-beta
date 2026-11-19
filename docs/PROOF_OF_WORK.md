# Proof-of-work log

Dates are blank where the source material does not establish a date. Entries distinguish direct observations from hypotheses and proposed next steps.

## 01 — Original scooter electronics inspection

- **Date:**
- **Hypothesis / reasoning:** The original display/middle electronics assembly contains separable functions (display, communications, GPS/LTE, connector interface) that can be documented and potentially replaced independently.
- **What I did:** Collected photographs of the scooter enclosure, display, connector panel, and multiple sides of the original green PCBs.
- **How I did it:** Visual inspection and photo documentation; board markings and component labels were read from close-up images where legible.
- **What happened / observed result:** The photo set shows a multi-board assembly, a connector panel with nine labeled ports, and a PCB carrying a MeigLink SLM750 LTE module. The main board has visible test pads and labels including BMS-TX, BMS-RX, DB-RX, MCU-TX, MCU-RX, 3V3, GND, 12V and other power/signal labels. Exact electrical behavior has not yet been established.
- **What I would change:** Photograph both sides square-on with a ruler, capture connector part numbers, transcribe every readable silkscreen label, and build a continuity/voltage measurement table before drawing a pin-accurate schematic.

## 02 — Nine-port connector function inventory

- **Date:**
- **Hypothesis / reasoning:** The molded/printed labels on the rear connector panel provide a useful first-pass functional map for a replacement harness.
- **What I did:** Recorded the nine port labels and their physical order.
- **How I did it:** Read the connector-panel labels from the supplied photographs and retained the user's confirmation that the labels and color coding correspond to the connector functions.
- **What happened / observed result:** The documented labels are USB DEBUG, BRAKE, THROTTLE, SPEAKER, LED, DATA, 5V OUTPUT, 12V OUTPUT, and FRONT LIGHT. This is a functional label inventory, not a verified electrical pinout. Polarity, voltage, current capability, signal direction, and protocol remain unmeasured.
- **What I would change:** Create a numbered breakout harness and use a current-limited bench supply and multimeter to characterize each pin. Record connector face orientation and wire colors in photographs.

## 03 — Battery label documentation

- **Date:**
- **Hypothesis / reasoning:** Correct battery voltage range is essential to selecting a safe replacement DC/DC power stage and compatible motor controller.
- **What I did:** Inspected and transcribed the battery label photograph.
- **How I did it:** Read the visible printed voltage, capacity, energy, and series/parallel text.
- **What happened / observed result:** The label visibly states 46.8 V / 15 Ah and 702 Wh. The smaller cell-configuration text appears to read 16S6P, but is blurry and appears inconsistent with the stated nominal voltage. The image alone does not establish chemistry, BMS limits, or maximum charge voltage.
- **What I would change:** Obtain the exact battery model/specification sheet, photograph the label in focus, inspect BMS documentation, and measure pack voltage with a suitable meter. Do not select the converter or controller from the nominal label alone.

## 04 — ESP32 replacement-board hypothesis

- **Date:**
- **Hypothesis / reasoning:** A custom PCB centered on an ESP32-S3 may replace dashboard/comms functions while preserving the existing motor controller, if interfaces can be safely characterized.
- **What I did:** Developed a block-level replacement-board concept with power regulation, protected inputs, communication expansion, and switched outputs.
- **How I did it:** Mapped the nine labeled functions to candidate interface categories: digital inputs, ADC conditioning, UART/data, buzzer driver, LED/light drivers, and regulated auxiliary power.
- **What happened / observed result:** A plausible architecture was identified, but no connector signal was measured and no firmware or hardware has been tested. A 36 V-class controller was previously discussed; compatibility with the photographed 46.8 V battery has not been established and must not be assumed.
- **What I would change:** Keep the first revision read-only/monitoring-focused. Do not control throttle, braking, or traction. Verify each signal with an oscilloscope/meter and use isolation or level shifting where appropriate.

## 05 — Replacement PCB 3D concept (Model 1: board only)

- **Date:** 2026-11-19
- **Hypothesis / reasoning:** A detailed board-only concept can help plan component zones, connector placement, mounting, and service access before committing to CAD.
- **What I did:** Generated a visual concept for an ESP32-S3 replacement PCB with a vehicle connector, power conversion, USB programming, protected interfaces, expansion headers, status LEDs, and mounting holes.
- **How I did it:** Used an image-generation workflow to create a technical-style multi-view illustration.
- **What happened / observed result:** A useful visual layout concept was produced. Its depicted 107 × 38 mm dimensions, component positions, connector geometry, and electrical labels are illustrative placeholders—not measurements taken from the original board and not validated engineering data.
- **What I would change:** Replace all guessed dimensions with measured board/enclosure geometry, select actual footprints and components, then build a KiCad schematic and PCB layout with design-rule checks.

## 06 — Controller enclosure 3D concept (Model 2: assembly)

- **Date:** 2026-11-19
- **Hypothesis / reasoning:** An exploded assembly view can help understand the relationship between the display cover, gasket, display PCB, main replacement PCB, connector interface, and rear enclosure.
- **What I did:** Generated a multi-view conceptual 3D teardown/assembly illustration.
- **How I did it:** Used an image-generation workflow based on the available photos and the previously discussed board architecture.
- **What happened / observed result:** A visual assembly concept was produced. Dimensions, internal stack-up, fasteners, board outlines, and the exact arrangement shown are not verified against physical measurements.
- **What I would change:** Measure the actual enclosure, standoffs, board outlines, display window, connector positions, and cable bend radii. Rebuild the assembly in mechanical CAD using real component STEP models.

## Overall result to date

The work has progressed from visual hardware inventory to a proposed ESP32-S3 replacement-board architecture and two visual design concepts. It has **not** yet reached verified reverse-engineering, electrical schematic capture, PCB fabrication, firmware integration, or powered vehicle testing.

## Next actions

1. Confirm battery chemistry, cell configuration, BMS limits, and maximum charge voltage.
2. Identify the exact motor controller model and its permitted battery-voltage range.
3. Measure the original board and enclosure.
4. Map every connector pin electrically with a safe breakout harness.
5. Identify serial protocols and logic voltage levels.
6. Create a verified schematic and PCB in KiCad.
7. Bench-test the new board without connecting throttle/motor control.
8. Validate enclosure fit and connector mating before any vehicle installation.
