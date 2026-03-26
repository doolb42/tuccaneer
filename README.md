# tucCANeer

A lightweight Python framework for reading and writing CAN bus messages on Hyundai/Kia/Motor Company (HKMC) PHEV and EV platforms, running on a Raspberry Pi with SocketCAN-compatible hardware.

## What it does

HKMC PHEVs reset driver-configurable settings — regenerative braking level, drive mode — on every ignition cycle with no manufacturer-provided way to persist them. tucCANeer fixes this by decoding CAN bus traffic via DBC files and sending the correct messages at startup to restore user-defined defaults automatically.

Beyond startup defaults, tucCANeer exposes a simple Python API for reading vehicle state and sending control messages, which other tooling can build on.

## Hardware

Minimum requirement for the core use case:
- Raspberry Pi Zero 2W
- MCP2515 CAN chip
- OBD-II to DB9 cable

A Pi 4B or greater is needed if you want to run display tooling on top of the framework.
The base framework hardware listed above can be purchased for ~£10

## Design

tucCANeer has no opinion on display, input, or physical controls. It handles the CAN layer and publishes vehicle state to a Redis pub/sub bus. Anything that wants to read state or send commands uses `api.py`. What you build on top of that is up to you. Use this framework at your own risk. I accept no responsibility for anything you do.

## Status

Pre-development. Primary development platform is a 2024 Hyundai Tucson PHEV. Compatibility with other HKMC PHEV/EV platforms (Ioniq, Kona, Niro, Sportage) is expected given shared architecture but unverified.

## Licence

MIT
