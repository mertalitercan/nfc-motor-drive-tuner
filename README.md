# NFC Motor Drive Tuner

An Android application that configures electric motor drive parameters wirelessly over NFC.
Built on STMicroelectronics' open-source ST25 NFC reference app and extended for production
use by **UHT Elektronik** as part of a **$105K government-funded project**.

> **Note:** The source code is not in this repository due to corporate confidentiality.
> This README documents the work and the improvements made over the reference app.

---

## What it does

Industrial motor drives expose dozens of configurable parameters (speed limits, torque curves,
fault thresholds, protection settings). Configuring them traditionally means a wired interface
and a technician operating from a PC.

This app lets a field technician tap their phone against the ST25 NFC tag on the drive's
controller and:

- **Read** the drive's current parameter set, decoded into human-readable values.
- **Modify** parameters through a guided UI.
- **Write** the new configuration back in a single synchronized session.

No cables. No memory-map lookups. No raw hex.

---

## Why it exists

The stock STMicroelectronics ST25 reference Android app is a general-purpose NFC tag tool:
pick a memory address, read or write one byte at a time, see the raw bytes. For a motor
drive with many bytes of configuration spread across multiple memory regions, that workflow
is impractical and error-prone in the field.

UHT Elektronik (Developer: Mertali Tercan) built an app that engineers could actually use on a job site. This project
takes the open-source ST25 codebase as a starting point and turns it into a purpose-built
configuration tool for their drives.

---

## Improvements over the reference app

| Area | ST25 reference app | This app |
| --- | --- | --- |
| Transfer size | Single-byte reads/writes | **Multi-byte transfers** |
| Memory addressing | Manual address entry by the operator | **Automated data mapping** |
| Read/write flow | Separate operations on raw bytes | **Synchronized session** with processed values shown during read |
| Data presentation | Raw bytes | Decoded values |
| Configuration accuracy | Operator-dependent | **100% accuracy** (verified against drive spec) |
| Memory footprint | Baseline | **~24% lower** RAM usage |
| UI/UX | Developer-facing | Redesigned for field use |

---

## Tech stack

- **Language:** Java
- **Platform:** Android (Android SDK)
- **NFC:** STMicroelectronics ST25 SDK
- **UI:** Android XML layouts
- **Build:** Gradle

---

## Demo

A demo video comparing the stock ST25 app and this version, configuring the same drive
side-by-side, will be added here.

---

## Author

**Mertali Tercan** — [mertalitercan.com](https://mertalitercan.com) · [LinkedIn](https://www.linkedin.com/in/mertali-t) · [GitHub](https://github.com/mertalitercan)

Delivered to **UHT Elektronik** for a government-funded industrial automation project.

---

## License & attribution

© All rights reserved by **UHT Elektronik** and **STMicroelectronics** (source provider).
This repository contains documentation only; no source code is distributed.
