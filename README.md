# VEO / COSMO scooter-e-bike reverse-engineering & ESP32 replacement-board proof of work

**Status:** Research / concept / draft beta. Not a validated retrofit.  
**Project owner:** TurnFlockOff / turnflockoff  
**Dates:** Intentionally left blank wherever the source record does not establish a date.

This repository records the observed hardware, the reverse-engineering approach, the proposed ESP32 replacement dashboard/controller-interface board, generated concept illustrations, open questions, and the next validation steps.

> **Safety and evidence notice:** Photos and measurements are evidence; interpretations are labeled as such. Generated wiring diagrams and 3D renders are concept artwork, not verified schematics, pinouts, CAD, or manufacturing files. Do not use them to wire a live scooter. No traction-control, throttle, brake, battery, or motor-controller modification is approved by this draft.

## Start here

- [Proof-of-work log](docs/PROOF_OF_WORK.md) — hypothesis, actions, method, observations, changes.
- [Reverse-engineering notes](docs/REVERSE_ENGINEERING_NOTES.md) — board markings, connector labels, battery evidence, uncertainties.
- [Replacement board concept](docs/REPLACEMENT_BOARD_CONCEPT.md) — proposed architecture and 3D concept scope.
- [Safety and validation plan](docs/SAFETY_AND_VALIDATION.md) — required checks before any powered test.
- [Evidence image register](evidence/IMAGE_REGISTER.md) — currently accessible photo/render inventory.
- [System block diagram](diagrams/system-block.svg) — conceptual architecture only.

## Current working hypothesis

The original middle electronics board may be replaceable with a custom interface PCB centered on an ESP32-S3, provided the original connector functions, signal levels, power rails, communications protocol, physical dimensions, and controller compatibility are first measured and documented. The intended result is a custom dashboard/app platform while retaining a separately compatible motor controller and its safety-critical protections.

## Important correction / unresolved battery detail

The battery photo visibly shows **46.8 V, 15 Ah, 702 Wh**. The small series/parallel text appears to read **16S6P** in the available photo, but that marking is not sufficiently clear and appears inconsistent with a conventional 46.8 V nominal lithium-ion pack. Do not assume the pack's full-charge voltage or cell configuration from this photo alone. Confirm the exact battery model, chemistry, BMS specification, and measured fully charged voltage before selecting a DC/DC converter or controller.

## Repository status

This is an evidence-and-design notebook. No validated KiCad schematic, PCB layout, firmware, app source, verified connector pinout, or tested replacement board is claimed to exist unless later committed with supporting evidence.
