# Safety and validation plan

## Do not connect or power the prototype from the scooter yet

This project involves a lithium battery pack, motor controller, throttle, brake inputs, and vehicle lighting. Incorrect wiring can damage equipment or cause unintended movement, fire, or loss of braking.

## Critical compatibility checks

- Confirm the battery chemistry, series count, maximum charge voltage, BMS current rating, and low-voltage cutoff.
- Confirm the motor controller's supported nominal and maximum battery voltage. A controller described as 36 V must not be assumed compatible with a battery labeled 46.8 V.
- Confirm polarity and ground reference before connecting any auxiliary converter.
- Select a DC/DC converter using the confirmed maximum battery voltage plus appropriate transient margin, not nominal voltage alone.
- Fuse the auxiliary power branch close to its source.
- Verify converter output under load before attaching electronics.

## Signal-interface checks

- Never connect an unknown vehicle signal directly to an ESP32 GPIO or ADC.
- ESP32 GPIO is 3.3 V logic and is not 5 V tolerant.
- Determine whether each signal is analog, open-drain, push-pull, switched battery voltage, or a serial bus.
- Use dividers, buffers, optocouplers, or transceivers only after the electrical behavior is known.
- Do not bypass brake cutoffs, throttle plausibility checks, controller interlocks, or BMS protections.
- Do not use the ESP32 as the sole safety controller for propulsion or braking.

## Bench validation sequence

1. Inspect the battery and controller labels and obtain manufacturer specifications.
2. Use a fused, current-limited bench supply for isolated board bring-up where possible.
3. Test the DC/DC stage with a dummy load.
4. Verify 5 V and 3.3 V rails, ripple, startup, and thermal rise.
5. Program and test ESP32 with no vehicle harness connected.
6. Test each input using a signal generator or controlled fixture.
7. Test output drivers with dummy loads, not vehicle lamps or actuators initially.
8. Verify communications using a logic analyzer/oscilloscope and documented bus settings.
9. Perform mechanical fit checks with the scooter powered off and battery disconnected.
10. Only proceed to supervised vehicle testing after a documented electrical and mechanical review.

## Evidence required before calling it plug-and-play

- Measured pinout and connector drawings
- Verified battery/controller compatibility
- Complete schematic and PCB design files
- BOM and component ratings
- Bench test logs
- Firmware version and source
- Fit-check photos and measured clearances
- Fail-safe behavior tests
- Independent review of any safety-critical control changes

## Current status

Not tested on a powered vehicle. No claim of plug-and-play compatibility is made.
