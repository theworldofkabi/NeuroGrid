# NeuroGrid – Edge-Based Agricultural IoT System

Domain: Internet of Things (IoT)
Use case: Smart agriculture in rural areas with unstable internet connectivity

## What this prototype shows
Sensors -> ESP32 edge device -> Adaptive spike encoding -> Local storage (offline)
-> Network quality check -> Intelligent sync scheduler -> Priority-based sync -> Central dashboard

All sensor data (soil moisture, temperature, humidity, rainfall) is SIMULATED in software.
No physical ESP32 hardware is needed.

## How to run
1. Unzip the folder.
2. Double-click `index.html` (opens in Chrome / Edge / Firefox). No install, no server.

## Demo flow (1-2 minutes)
1. Generate Sensor Data (a few times)
2. Simulate Network Failure
3. Generate Sensor Data (readings get stored locally, pending count rises)
4. Restore Network (system evaluates network quality)
5. Start Sync (Critical -> High -> Normal)
6. Show Statistics page

## Priority rules (in index.html, function computePriority)
- Soil moisture <= 18%  -> Critical
- Rainfall >= 28 mm     -> High
- Otherwise             -> Normal

## Connecting real hardware later
Replace `generateReading()` in index.html with a fetch()/MQTT-over-WebSocket
call that receives real ESP32 readings, then pass them to the same record pipeline.

## Files
- index.html : complete prototype (HTML + CSS + JavaScript)
- README.md  : this file
