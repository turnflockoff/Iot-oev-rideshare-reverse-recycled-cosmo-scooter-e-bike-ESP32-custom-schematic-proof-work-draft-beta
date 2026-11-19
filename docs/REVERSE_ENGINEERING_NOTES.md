# Reverse-engineering notes

## Scope

The project is investigating the original V-E0-style scooter/e-bike display and middle electronics assembly as a candidate for a custom ESP32-based replacement. The intended app/dashboard is a later software layer. The motor controller and battery must remain independently compatible and protected.

## Observed from the photo set / conversation

### Connector panel

The nine functional labels recorded from the panel are:

| Port | Label | Candidate interface role | Verification status |
|---:|---|---|---|
| 1 | USB DEBUG | Programming/debug interface | Label observed; electrical details unknown |
| 2 | BRAKE | Brake-state input/interface | Label observed; voltage/polarity unknown |
| 3 | THROTTLE | Throttle interface | Label observed; signal range/protocol unknown |
| 4 | SPEAKER | Buzzer/speaker interface | Label observed; drive requirements unknown |
| 5 | LED | LED interface | Label observed; voltage/current unknown |
| 6 | DATA | Communications interface | Label observed; protocol unknown |
| 7 | 5V OUTPUT | Auxiliary 5 V rail | Label observed; regulation/current capacity unverified |
| 8 | 12V OUTPUT | Auxiliary 12 V rail | Label observed; regulation/current capacity unverified |
| 9 | FRONT LIGHT | Front-light interface | Label observed; switched polarity/current unknown |

The user stated that the molded labels and color coding on the back are correct. This is useful evidence for function naming, but it does not establish individual pin polarity, electrical levels, or connector internals.

### Main PCB markings / test labels

Previously transcribed from the supplied PCB photographs:
- PCB markings include **SL2550_N02** and **T670VC_MB_V1.02_PCB** on a board.
- A MeigLink **SLM750 LTE** module is visible on the original electronics.
- Test/silkscreen labels include **BMS-TX, BMS-RX, SPK-/SPK+, DB-RX, DIO, MCU-TX, MCU-RX, 3V3, GND, 12V, 12V-LED, BRAKE-BAT, VDD5V** and other labels that need a sharper transcription.
- These labels suggest several power, serial, speaker, and controller interfaces; they do not prove signal direction or protocol.

### Battery label

The supplied photo visibly shows:
- 46.8 V
- 15 Ah
- 702 Wh

The smaller cell configuration appears to read “16S6P” but the photo is not sufficiently sharp to treat that transcription as certain. It appears inconsistent with a conventional 46.8 V nominal lithium-ion configuration. Resolve this discrepancy using the battery model documentation and BMS specifications. Do not assume a 54.6 V maximum charge voltage unless the pack is confirmed to be a 13-series lithium-ion pack.

## Inferences (not confirmed)

- The original middle board may combine display, communications, GPS/LTE, auxiliary power, and interface functions.
- A custom ESP32-S3 board could potentially replace selected dashboard/comms functions.
- Some labeled ports may be analog, digital, switched-power, or serial interfaces.
- A separate motor controller may handle the high-current motor phase and battery functions.

## Unknowns requiring measurements

1. Exact battery chemistry, series count, full-charge voltage, low-voltage cutoff, BMS current limits.
2. Exact motor controller model and supported voltage range.
3. Board dimensions, thickness, mounting-hole centers, component heights, connector positions.
4. Connector pin numbering/orientation, pin count, mating part numbers, wire gauge.
5. Voltage and polarity on every connector pin.
6. Brake and throttle signal electrical characteristics.
7. DATA bus protocol, baud rate, framing, voltage, and message semantics.
8. Whether 5 V and 12 V outputs are always-on, switched, or sourced by the original board.
9. Whether any functions are safety-critical or require OEM interlocks.
10. Whether the original display communicates with the main board using UART, CAN, or a proprietary protocol.

## Measurement discipline

For each pin, record: connector ID, pin number, face orientation, wire color, measured voltage to confirmed ground, behavior with key on/off, behavior under relevant safe conditions, instrument used, and confidence level. Do not probe unknown pins by shorting them or connecting them directly to ESP32 GPIO.
