# Research log — hypothesis, method, outcome, changes

This log distinguishes available evidence from inference. Unknown dates remain blank.

## Shared e-bike electrical architecture
- **Date:** 2026-07-12 (saved illustration timestamp)
- **Hypothesis:** A shared e-bike can be represented as traction-power and control/telematics layers: battery/BMS, fuse/relay distribution, motor controller, display, sensors, and GPS/cellular/Bluetooth modules.
- **What I did:** Created a high-level conceptual wiring architecture with connector labels, wire-color legend, sensor connections, dashboard, telematics, and diagnostic-port blocks.
- **What happened:** Produced a broad system map. It is not a verified OEM schematic; labels, connector assignments, and wire colors remain illustrative.
- **What I would change:** Replace assumed connections with measured records tied to a specific vehicle revision; add source-photo references and confidence ratings for each net.

## E-bike electrical schematic design
- **Date:** 2026-07-12 (saved illustration timestamp)
- **Hypothesis:** Bike controls and cockpit may communicate with a motor controller and telematics unit over low-voltage signals such as UART or CAN, while power distribution is separate.
- **What I did:** Drafted a schematic showing battery/BMS, motor/controller, throttle, brake levers, torque/cadence sensors, display, telematics, GPS/LTE/Bluetooth, and service connector.
- **What happened:** Produced a structured reference diagram. No captured bus traffic, confirmed connector pinout, or electrical measurements accompany it.
- **What I would change:** Add connector-by-connector measurement sheets, protocol captures, and verified/unknown markers for each signal.

## Conceptual shared electric-bike wiring diagram
- **Date:** 2026-07-12 (saved illustration timestamp)
- **Hypothesis:** Major electrical domains can be documented as battery/power, propulsion, controls/sensors, dashboard, and telematics.
- **What I did:** Built a conceptual multi-connector wiring diagram and legend.
- **What happened:** Produced an educational architecture map, not manufacturer documentation.
- **What I would change:** Validate fuse sizes, voltage domains, relay behavior, and connector functions against physical evidence before treating any value as actionable.

## E-scooter display/control module guide
- **Date:** 2026-07-20 (saved illustration timestamp)
- **Hypothesis:** The display/control module may be a multi-board assembly with display/keypad PCB, main processor/power PCB, connector block, backup cell, and enclosure.
- **What I did:** Created a teardown-style guide, exploded assembly, connector overview, test-point ideas, and staged inspection/rebuild sequence.
- **What happened:** Produced a visual inspection aid. Board details and test points are not independently verified; connector pin count and pinout may vary.
- **What I would change:** Base teardown notes on original high-resolution photos of both PCB sides, board markings, and continuity/voltage measurements. Do not energize from inferred pinouts.

## Display Control Module Teardown Guide
- **Date:** 2026-08-03 (saved file timestamp)
- **Hypothesis:** A separate display PCB and main PCB may exchange display/keypad data while the main board handles power and external I/O.
- **What I did:** Organized a teardown-style illustration with PCB sides, likely regulators/MCU, connectors, test pads, enclosure parts, and functional blocks.
- **What happened:** Created a component-identification reference. Labels are interpretations, not confirmed component-level analysis.
- **What I would change:** Photograph actual boards under consistent lighting, transcribe readable IC markings, and verify candidate functions by datasheet and non-destructive measurements.

## ESP32 Smart E-Bike Dashboard Blueprint
- **Date:** 2026-08-05 (saved file timestamp)
- **Hypothesis:** An independent ESP32 dashboard could provide speed display, battery/status UI, buttons, indicators, and optional sensor/controller data without depending on the original display electronics.
- **What I did:** Drafted an ESP32-WROOM-based architecture, display mockup, PCB concept, connector/pinout concept, mounting enclosure, and bill-of-materials section.
- **What happened:** Produced a design concept. No assembled prototype, firmware, validated PCB, or vehicle test result was found in the available record.
- **What I would change:** Start with a low-voltage bench prototype and simulated inputs; add isolated UART/CAN interfaces only after confirming target-controller electrical specifications.

## ESP32 Dashboard Replacement Wiring Guide
- **Date:** 2026-09-27 (saved file timestamp)
- **Hypothesis:** A standalone dashboard can be powered through a properly rated DC-DC converter and communicate with compatible controller signals while reading independent brake/speed inputs.
- **What I did:** Created a conceptual guide showing battery, fuse/main switch, controller, DC-DC conversion, ESP32, display, buttons, sensors, buzzer, LEDs, and lighting.
- **What happened:** Produced a planning diagram with explicit warnings that original V-E0 connections and pinouts are unverified. It does not prove compatibility or safe direct connection.
- **What I would change:** Use the exact controller model and datasheet; document measured voltage/current and logic levels; keep traction wiring separate from low-voltage prototyping.

## Electric Scooter Controller Exploded CAD Infographic
- **Date:** 2026-09-27 (saved file timestamp)
- **Hypothesis:** The scooter display/controller assembly may be documented as an enclosure, display PCB, main controller PCB, GPS antenna section, connector interface, and protective cover.
- **What I did:** Created an exploded CAD-style concept with front/rear/side views, component stack, dimensions, and a nine-port connector illustration.
- **What happened:** Produced a visual assembly hypothesis. Dimensions, materials, board architecture, ESP32-S3 references, and connector functions are not verified manufacturer data.
- **What I would change:** Re-measure the physical assembly with calipers, photograph fasteners and board identifiers, and label render-only details as estimates until verified.

## Original vehicle-photo recovery
- **Date:** 
- **Hypothesis:** Earlier project materials may contain original Cosmo, Astro, and Apollo vehicle photographs alongside engineering work.
- **What I did:** Searched available conversation and Library files for V-E0, Cosmo, Astro, Apollo, scooter/e-bike, PCB, and reverse-engineering terms.
- **What happened:** Recovered engineering illustrations listed in the inventory, but did not recover the original Cosmo/Astro/Apollo vehicle photographs or a complete source-photo set.
- **What I would change:** Add original vehicle photographs and source notes when recovered, preserving original filenames and capture dates.

## Overall conclusion
The defensible description is that this work developed a reverse-engineering **research plan and conceptual redesign**, centered on understanding a V-E0 shared-ride display/control assembly and exploring an independent ESP32 dashboard. The available record does not prove successful reverse engineering or a working scooter modification. The next milestone should be a documented, safe, non-invasive measurement and bench-test package.
