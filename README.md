<p align="center">
    <br>
    <!-- <img src="" width="400"/> -->
    <br>
<p>

<div align="center">

[![license](https://img.shields.io/github/license/Nuliu-Z/keyboard-friend)](https://github.com/Nuliu-Z/keyboard-friend/blob/main/LICENSE)
[![GitHub pull-requests](https://img.shields.io/github/issues-pr/Nuliu-Z/keyboard-friend.svg)](https://GitHub.com/Nuliu-Z/keyboard-friend/pull/)
[![GitHub latest commit](https://badgen.net/github/last-commit/Nuliu-Z/keyboard-friend)](https://GitHub.com/Nuliu-Z/keyboard-friend/commit/)

<!-- [Discord](https://discord.gg/) -->


<h4 align="center">
    <p>
    <b> English </b>
      <a href="https://github.com/Nuliu-Z/keyboard-friend/blob/main/README_zh.md">中文</a>
    <p>
</h4>

</div>


# keyboard-friend · One Press to Trigger Your Commands

## Introduction

This is a simple and practical macro keyboard.
What makes it special?

- **Configuration-friendly** – No additional driver installation required
- **DIY-friendly** – Few parts, easy to buy and assemble
- **Cross-platform** – Supports Windows, Linux, and Android

---

## Hardware & Firmware

For experienced users, it is recommended to purchase components and build your own.

For those who want to directly experience the features, it is recommended to purchase the ready-made product (coming soon), and you can skip the "DevHardwareice and Firmware" section.

| Component               | Description                         | Price (CNY) |
| ----------------------- | ----------------------------------- | ----------- |
| 4×4 I2C Matrix Keypad   | 16-key layout, supports I2C comms   | 14          |
| nRF52840 ProMicro       | Main controller board               | 12          |
| USB Type-C Cable        | Power + data transfer               | -           |

Note: Flashing firmware also requires J-Link/DAPLink or other general-purpose firmware development devices

4×4 I2C Matrix Keypad

<img src="assets/keyboard-module-matrix-i2c.png" alt="keyboard-module-matrix-i2c" width="300">

nRF52840 ProMicro

<img src="https://www.nologo.tech/assets/img/other/NRF52840/ProMicroNRF52840.jpg" alt="nRF52840 ProMicro" width="300">

### Hardware Wiring

| 4×4 I2C Matrix Keypad | nRF52840 ProMicro |
| --------------------- | ----------------- |
| VCC                   | VCC               |
| GND                   | GND               |
| SCL                   | P0.27             |
| SDA                   | P0.26             |
| INT                   | Not Connected     |

Host USB Port <--USB Cable--> nRF52840 ProMicro Type-C

### Flashing Firmware

Download the firmware and flash it via J-Link

If you're not familiar with J-Link command, you can use [nRF Connect for Desktop (Programmer app)](https://docs.nordicsemi.com/bundle/swtools_docs/page/app/pc-nrfconnect-programmer/index.html), or ask AI "How to download hex format firmware to nrf52840" :)

For the firmware list, see [Releases](https://github.com/Nuliu-Z/keyboard-friend/releases).

---

## Quick Start

Get started in two steps

### Configuration Mode – Edit the config file to set the keypress content you want

Press the `*` key three times in a row to trigger mode switching. In "Configuration Mode", the device will be recognized as a USB drive on the host. Open the USB drive and modify/create the `config.json` file.

`config.json` file field descriptions:
- `name`: Configuration file description, can be any text
- `0-9, A-D, *, #`: Mapped to custom strings
  - Supported: Letters (a-z, A-Z), numbers (0-9), common symbols (- _ @ # $ % ^ & * etc.)
  - Supported special characters: `\n` (newline), `\t` (tab), `\b` (backspace)
  - Does not support multi-byte characters such as Chinese, Japanese, emoji
  - String length ≤ 64 bytes
- Multiple backup configuration files can be stored (e.g., `config_mode1.json, config_mode2.json, ...`), but only `config.json` will be loaded

Example
```json
{
    "name": "keypad_config_v1",
    "0": "hello 0",
    "1": "hello 1",
    "2": "hello 2",
    "3": "hello 3",
    "4": "hello 4",
    "5": "hello 5",
    "6": "hello 6",
    "7": "good 7",
    "8": "good 8",
    "9": "good 9",
    "A": "good A",
    "B": "good B",
    "C": "good C",
    "D": "good D",
    "*": "good *",
    "#": "good #"
}
```

### Working Mode – Connect the device and press the corresponding keys to trigger

Press the `*` key three times in a row to trigger mode switching. In "Working Mode", the device will be recognized as a keyboard on the host. Press a key in any text input field to output the corresponding content.

---

## Template Configuration

Switch to "Configuration Mode", copy the configuration to the device and name it `config.json`, then switch to "Working Mode" to use it.

---

## Limitations

- Does not support Chinese character input
- Does not support wireless connection (requires wired use)

---

## Thanks & Open Source

The project pays tribute to classic games. Forks and PRs are welcome.
Apache License © 2026
