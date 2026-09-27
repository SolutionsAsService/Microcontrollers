# Embedded Hardware Encyclopedia

A practical, structured reference for microcontrollers, development boards, sensors, displays, RFID/NFC readers, cameras, communication modules, power components, and other embedded hardware.

The goal is simple:

> **Know what the hardware does, know what every pin does, know what can safely connect to it, and eventually be able to simulate it before building it.**

---

## What This Repository Is

This repository is the foundation for a broader **Embedded Hardware Encyclopedia + Virtual Hardware Lab**.

It combines:

- Microcontroller references
- Development board references
- Pinout documentation
- Peripheral documentation
- Sensor references
- Display references
- RFID/NFC hardware
- Camera modules
- Communication interfaces
- Power components
- Secure elements
- Hardware wallet components
- Wiring references
- Machine-readable hardware definitions
- Virtual hardware simulation

The long-term goal is to make hardware information useful to both humans and software.

```text
Hardware Encyclopedia
        │
        ├── Documentation
        │
        ├── Pin Definitions
        │
        ├── Component Data
        │
        ├── Wiring Information
        │
        ├── Compatibility Rules
        │
        ├── Virtual Hardware Lab
        │
        └── Hardware Configuration Tools
````

---

# Repository Structure

The repository is organized around hardware categories rather than individual projects.

```text
embedded-hardware/
│
├── README.md
├── index.html
├── styles.css
│
├── microcontrollers/
│   ├── esp32/
│   ├── esp32-s3/
│   ├── esp8266/
│   ├── arduino/
│   ├── stm32/
│   ├── rp2040/
│   ├── rp2350/
│   └── nrf52/
│
├── displays/
│   ├── lcd/
│   ├── oled/
│   ├── ssd1306/
│   └── sh1106/
│
├── nfc-rfid/
│   ├── rc522/
│   ├── pn532/
│   └── other-readers/
│
├── cameras/
│   ├── ov7670/
│   ├── ov2640/
│   ├── ov5640/
│   └── other-modules/
│
├── sensors/
│   ├── temperature/
│   ├── humidity/
│   ├── motion/
│   ├── pressure/
│   ├── light/
│   └── environmental/
│
├── communication/
│   ├── i2c/
│   ├── spi/
│   ├── uart/
│   ├── can/
│   ├── rs485/
│   ├── usb/
│   ├── bluetooth/
│   └── wifi/
│
├── security/
│   ├── secure-elements/
│   ├── authentication/
│   └── cryptography/
│
├── power/
│   ├── regulators/
│   ├── chargers/
│   ├── batteries/
│   └── power-monitors/
│
├── components/
│   ├── buttons/
│   ├── encoders/
│   ├── relays/
│   ├── motors/
│   ├── buzzers/
│   └── leds/
│
├── projects/
│   ├── hardware-wallet/
│   ├── embedded-lab/
│   └── reference-projects/
│
└── data/
    ├── microcontrollers/
    ├── boards/
    ├── displays/
    ├── sensors/
    ├── readers/
    └── components/
```

The exact directory structure may evolve as the encyclopedia grows.

---

# Core Philosophy

This project is not intended to be another collection of random pinout diagrams.

Each hardware entry should answer five questions:

1. **What is this?**
2. **What are its electrical requirements?**
3. **What does every important pin/interface do?**
4. **What can I connect it to?**
5. **What can go wrong?**

For example:

```text
ESP32
 │
 ├── GPIO
 ├── ADC
 ├── DAC
 ├── PWM
 ├── UART
 ├── SPI
 ├── I2C
 ├── I2S
 ├── Touch
 ├── RTC
 ├── Boot Strapping
 └── Power
```

The encyclopedia should document the actual engineering implications of those features, not just list them.

---

# Hardware Categories

## Microcontrollers

Microcontrollers are the brains of embedded systems.

Examples:

* ESP32
* ESP32-S2
* ESP32-S3
* ESP32-C3
* ESP32-C6
* ESP8266
* Arduino Uno
* Arduino Nano
* STM32
* RP2040
* RP2350
* nRF52

Each MCU entry should document:

* architecture
* CPU
* clock
* memory
* GPIO
* ADC
* DAC
* PWM
* timers
* interrupts
* UART
* SPI
* I2C
* I2S
* USB
* wireless
* RTC
* boot configuration
* power requirements
* security features
* pin restrictions
* board/module differences

---

# Development Boards

An MCU and a development board are not necessarily the same thing.

For example:

```text
ESP32 SoC
    ↓
ESP32-WROOM Module
    ↓
Development Board
    ↓
USB
Voltage Regulator
Buttons
Headers
LEDs
```

Board documentation should distinguish:

* SoC
* module
* development board
* manufacturer
* board revision
* exposed GPIO
* onboard peripherals
* regulator
* USB interface
* oscillator
* flash
* PSRAM
* antenna
* boot buttons

This prevents the common problem of treating every "ESP32" board as electrically identical.

---

# Pin Documentation

Pin documentation is one of the most important parts of the repository.

A pin should not simply be documented as:

```text
GPIO 5
```

Instead:

```text
GPIO 5
├── Input: Yes
├── Output: Yes
├── Pull-up: Yes
├── Pull-down: Yes
├── PWM: Yes
├── SPI: Possible
├── Boot-sensitive: Yes
├── ADC: No
├── Recommended:
│   ├── Digital output
│   └── SPI CS
└── Caution:
    └── Boot configuration may matter
```

The objective is to make pin selection an engineering decision rather than guesswork.

---

# Machine-Readable Hardware Data

Human documentation is useful.

Structured data makes the encyclopedia much more powerful.

Eventually every major component should have a machine-readable definition.

Example:

```json
{
  "name": "ESP32",
  "category": "microcontroller",
  "architecture": "Xtensa",
  "logic_voltage": 3.3,
  "gpio": {
    "count": 34
  },
  "interfaces": {
    "uart": true,
    "spi": true,
    "i2c": true,
    "i2s": true
  }
}
```

A complete definition can become much more detailed:

```text
component
│
├── identity
├── manufacturer
├── part_number
├── family
├── package
├── electrical
├── power
├── gpio
├── adc
├── dac
├── pwm
├── timers
├── uart
├── spi
├── i2c
├── usb
├── wireless
├── boot
├── security
├── physical
├── compatibility
├── examples
├── warnings
└── sources
```

---

# Why Structured Data Matters

Once the hardware is represented as structured data, the same information can power multiple systems.

```text
                 Hardware JSON
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
   Documentation   Pin Tables   Virtual Lab
        │             │             │
        ▼             ▼             ▼
      Website    Compatibility   Simulation
```

Eventually:

```text
Hardware Definition
        ↓
Generate
        ↓
├── HTML documentation
├── Pinout tables
├── Wiring diagrams
├── Component selectors
├── Compatibility checks
├── Simulator models
└── Firmware configuration
```

---

# Components

The encyclopedia is not limited to MCUs.

Important component categories include:

## Displays

* 16x2 LCD
* 20x4 LCD
* SSD1306 OLED
* SH1106 OLED
* TFT displays
* e-paper

Document:

* resolution
* controller
* voltage
* interface
* pins
* addressing
* initialization
* current
* wiring
* libraries

---

## NFC / RFID

Examples:

* MFRC522
* RC522 modules
* PN532
* PN7150
* PN7160
* other NFC controllers

Document:

* frequency
* protocols
* supported card types
* SPI
* I2C
* UART
* IRQ
* reset
* power
* logic levels
* antenna
* range
* module differences

---

## Cameras

Examples:

* OV7670
* OV2640
* OV5640
* OV3660
* other camera modules

Document:

* sensor
* lens
* pixel formats
* control interface
* pixel interface
* XCLK
* PCLK
* VSYNC
* HREF
* data pins
* power
* regulator
* module-specific differences

Camera documentation should be particularly careful about unverified pinouts.

---

## Sensors

Examples:

* temperature
* humidity
* pressure
* accelerometers
* gyroscopes
* magnetometers
* light sensors
* distance sensors
* environmental sensors
* gas sensors

Document:

```text
Sensor
├── Measurement
├── Range
├── Accuracy
├── Voltage
├── Current
├── Interface
├── Address
├── Pins
├── Sampling
├── Calibration
└── Example Code
```

---

# Communication Interfaces

Interfaces should be documented independently from individual devices.

## I2C

```text
MCU
 │
 ├── SDA ───────────────┐
 └── SCL ───────────────┤
                        │
             ┌──────────┴──────────┐
             │                     │
           OLED                  Sensor
```

Important concepts:

* SDA
* SCL
* pull-ups
* address
* bus capacitance
* clock speed
* multiple devices
* address conflicts

---

## SPI

```text
MCU
 │
 ├── SCK
 ├── MOSI
 ├── MISO
 ├── CS ───── Device A
 └── CS ───── Device B
```

Document:

* clock
* MOSI
* MISO
* CS
* mode
* frequency
* voltage
* bus sharing

---

## UART

```text
MCU TX ───── RX Device
MCU RX ───── TX Device
GND ───────── GND
```

Document:

* baud rate
* TX
* RX
* parity
* stop bits
* flow control
* voltage levels

---

# Electrical Compatibility

One of the main purposes of the encyclopedia is preventing hardware damage.

Every component should document:

```text
Logic Voltage
Power Voltage
Maximum Voltage
Typical Current
Maximum Current
Input Tolerance
Output Drive
Pull-ups
Pull-downs
```

Example:

```text
MCU
3.3V Logic
   │
   X
   │
5V-only peripheral

Potential compatibility problem
```

Never assume that because two devices communicate using SPI or I2C they are electrically compatible.

---

# Pin Conflict Detection

A future tool should allow a user to select components:

```text
ESP32
+
SSD1306
+
RC522
+
Encoder
+
Buttons
```

The system could generate:

```text
PIN ASSIGNMENT

GPIO 21 → OLED SDA
GPIO 22 → OLED SCL

GPIO 18 → RC522 SCK
GPIO 19 → RC522 MISO
GPIO 23 → RC522 MOSI
GPIO 5  → RC522 CS

GPIO 32 → Encoder A
GPIO 33 → Encoder B
GPIO 25 → Encoder Button
```

Then detect:

```text
✓ No conflicts

or

⚠ GPIO 22 assigned to two devices

or

⚠ GPIO 12 is boot-sensitive

or

⚠ ADC2 conflicts with Wi-Fi usage
```

---

# Wiring Documentation

Every component should eventually have a wiring reference.

Example:

```text
ESP32                 SSD1306
─────                 ───────
3.3V ──────────────── VCC
GND  ──────────────── GND
GPIO21 ────────────── SDA
GPIO22 ────────────── SCL
```

And:

```text
ESP32                 RC522
─────                 ─────
3.3V ──────────────── VCC
GND  ──────────────── GND
GPIO18 ────────────── SCK
GPIO19 ────────────── MISO
GPIO23 ────────────── MOSI
GPIO5  ────────────── SS
GPIO27 ────────────── RST
```

Pin assignments should always be treated as examples unless explicitly defined for a particular board.

---

# Reference Projects

The encyclopedia also contains complete examples.

Examples:

```text
projects/
├── oled-status/
├── nfc-reader/
├── temperature-monitor/
├── esp32-web-server/
├── camera-viewer/
├── hardware-wallet/
└── embedded-lab/
```

Projects should show how documented components actually work together.

---

# Hardware Wallet

One major reference project is the NFC/RFID hardware wallet.

Conceptually:

```text
                    Hardware Wallet
                           │
              ┌────────────┼────────────┐
              │            │            │
             MCU       Secure Element   NFC
              │            │            │
              ├────────────┤            │
              │                         │
            OLED                    NFC Antenna
              │
         Buttons / Dial
```

The project demonstrates how the encyclopedia can describe a complete embedded product rather than isolated parts.

Components include:

* ESP-class MCU
* Secure Element
* NFC/RFID reader
* OLED
* buttons
* rotary encoder
* battery
* USB-C
* power management

---

# Virtual Hardware Lab

The long-term goal is to connect the encyclopedia to a browser-based hardware simulator.

```text
             Hardware Encyclopedia
                      │
                      ▼
              Hardware Definition
                      │
                      ▼
                Virtual MCU
                      │
        ┌─────────────┼─────────────┐
        │             │             │
       GPIO          I2C           SPI
        │             │             │
        ▼             ▼             ▼
     Button         OLED          NFC
```

A user should eventually be able to:

1. Select an MCU.
2. Add components.
3. Assign pins.
4. Write firmware.
5. Run the firmware.
6. Observe GPIO.
7. Observe serial output.
8. Observe displays.
9. Simulate sensors.
10. Detect conflicts.
11. Debug the design.

---

# Virtual Hardware Model

A component should eventually be able to expose a standard interface.

Example:

```js
{
  type: "display",
  name: "SSD1306",
  interface: "i2c",

  pins: {
    vcc: "power",
    gnd: "ground",
    sda: "i2c.sda",
    scl: "i2c.scl"
  },

  address: "0x3C"
}
```

The simulator can then understand the component without hardcoding every possible board.

---

# Documentation Standard

Every hardware page should attempt to contain:

```text
1. Overview
2. Exact Part Identification
3. Specifications
4. Pinout
5. Electrical Characteristics
6. Interfaces
7. Wiring
8. Example Code
9. Common Uses
10. Common Mistakes
11. Compatibility
12. Troubleshooting
13. Machine-Readable Definition
14. Sources
```

---

# Exact Part Identification

This is extremely important.

A module name does not always uniquely identify the underlying hardware.

For example:

```text
"ESP32 board"
"RC522 module"
"OLED 0.96"
"OV2640 camera"
```

may describe many different physical implementations.

Documentation should distinguish:

```text
Manufacturer
Part Number
Module
Board
Revision
Controller
Sensor
Connector
Voltage
```

If the exact hardware cannot be verified, the documentation should say so.

---

# Source of Truth

The repository should distinguish between:

### Verified

Information directly supported by:

* manufacturer documentation
* official datasheets
* reference manuals
* official schematics
* authoritative technical documentation

### Inferred

Information derived from:

* common module layouts
* known reference designs
* community documentation
* observed hardware

### Unknown

Information that has not been sufficiently verified.

Do not silently convert an inferred pinout into a canonical pinout.

---

# Accuracy Rules

## Rule 1

Never guess a pinout.

## Rule 2

Never assume two boards with the same marketing name are identical.

## Rule 3

Always distinguish MCU, module, and development board.

## Rule 4

Document voltage separately from communication protocol.

## Rule 5

Document boot-sensitive pins.

## Rule 6

Document pins consumed by onboard hardware.

## Rule 7

Document input-only pins.

## Rule 8

Document peripheral conflicts.

## Rule 9

Document board-specific differences.

## Rule 10

Mark uncertain information explicitly.

---

# Adding a New Microcontroller

Create:

```text
microcontrollers/<name>/
```

Recommended files:

```text
microcontrollers/
└── example-mcu/
    ├── index.html
    ├── example-mcu.json
    ├── pinout.svg
    └── README.md
```

The JSON should contain the canonical structured data.

The HTML should present that information to humans.

The SVG should provide the visual pinout.

The README should explain the component and documentation status.

---

# Adding a New Component

For a new component:

```text
components/<category>/<component>/
```

Example:

```text
components/
└── displays/
    └── ssd1306/
        ├── index.html
        ├── ssd1306.json
        ├── pinout.svg
        └── README.md
```

---

# Component Checklist

Before considering a component documented:

```text
[ ] Exact part identified
[ ] Manufacturer identified
[ ] Datasheet located
[ ] Voltage documented
[ ] Current documented
[ ] Pinout documented
[ ] Interfaces documented
[ ] Address documented
[ ] Electrical warnings documented
[ ] Example wiring included
[ ] Example code included
[ ] Common mistakes documented
[ ] Sources included
[ ] JSON definition created
[ ] HTML reference created
```

---

# Example Component Record

```json
{
  "id": "ssd1306-128x64-i2c",
  "name": "SSD1306 OLED",
  "category": "display",

  "controller": {
    "name": "SSD1306"
  },

  "display": {
    "width": 128,
    "height": 64,
    "technology": "OLED"
  },

  "interface": {
    "type": "I2C"
  },

  "pins": {
    "vcc": "power",
    "gnd": "ground",
    "sda": "i2c.sda",
    "scl": "i2c.scl"
  },

  "notes": [
    "Module voltage requirements must be verified.",
    "I2C address varies by module configuration."
  ]
}
```

---

# Recommended Naming

Use descriptive names.

Good:

```text
esp32-wroom-32
arduino-nano-atmega328p
ssd1306-128x64
mfrc522
pn532
ov2640
```

Avoid ambiguous names:

```text
esp32-new
oled1
rfid-module
camera
board-final
```

---

# File Naming

Prefer lowercase and predictable names.

```text
index.html
styles.css
component.json
pinout.svg
README.md
```

For special documentation:

```text
wiring.md
registers.md
protocol.md
examples.md
```

---

# Website

The encyclopedia is designed to work as a static documentation site.

Typical structure:

```text
index.html
styles.css

microcontrollers/
displays/
nfc-rfid/
cameras/
sensors/
communication/
security/
power/
components/
```

No database is required for the basic encyclopedia.

This makes it easy to:

* host statically
* deploy through GitHub Pages
* deploy through Vercel
* deploy through Cloudflare
* package locally
* mirror offline

---

# Design Philosophy

The documentation UI intentionally favors:

* black and white
* minimal visual noise
* strong typography
* responsive tables
* readable technical data
* mobile-friendly layouts
* fast loading
* static assets
* no unnecessary framework dependency

The goal is for the documentation to feel closer to a technical reference manual than a marketing website.

---

# Future Architecture

The eventual system can become:

```text
                         ┌───────────────────┐
                         │ Hardware Database │
                         └─────────┬─────────┘
                                   │
                    ┌──────────────┼──────────────┐
                    │              │              │
                    ▼              ▼              ▼
              Documentation    Pin Engine     Simulator
                    │              │              │
                    ▼              ▼              ▼
                  Website      Wiring Tool    Virtual Lab
                                   │
                                   ▼
                            Compatibility
                              Detection
```

Eventually:

```text
Hardware Database
       │
       ├── Encyclopedia
       │
       ├── Pinout Generator
       │
       ├── Wiring Generator
       │
       ├── BOM Generator
       │
       ├── Firmware Generator
       │
       ├── Virtual Hardware Lab
       │
       ├── PCB Planning
       │
       └── Hardware Validation
```

---

# Roadmap

## Phase 1 — Encyclopedia

* [x] Basic microcontroller references
* [x] ESP32 documentation
* [x] Arduino Nano documentation
* [x] Camera references
* [x] RFID/NFC references
* [x] OLED/LCD references
* [x] About / documentation philosophy
* [ ] Expand component catalog
* [ ] Add structured JSON

## Phase 2 — Structured Hardware Database

* [ ] Standard component schema
* [ ] Pin schema
* [ ] Electrical constraints
* [ ] Interface definitions
* [ ] Compatibility metadata
* [ ] Source tracking
* [ ] Hardware revision tracking

## Phase 3 — Wiring Engine

* [ ] Component selector
* [ ] MCU selector
* [ ] Automatic pin assignment
* [ ] Conflict detection
* [ ] Voltage compatibility checks
* [ ] Wiring diagram generation

## Phase 4 — Virtual Hardware Lab

* [x] Basic virtual MCU environment
* [x] Serial monitor
* [x] Virtual GPIO
* [x] Virtual OLED
* [x] Simulated Wi-Fi
* [ ] Hardware definition loader
* [ ] Virtual I2C
* [ ] Virtual SPI
* [ ] Virtual UART
* [ ] Virtual NFC
* [ ] Sensor simulation
* [ ] Component graph

## Phase 5 — Hardware Development Platform

* [ ] Firmware validation
* [ ] Pin configuration generation
* [ ] BOM generation
* [ ] PCB planning
* [ ] Wiring export
* [ ] Hardware test definitions
* [ ] Manufacturing test definitions

---

# Relationship to the NFC Wallet

The NFC/RFID hardware wallet is one of the primary real-world reference products for this repository.

Its architecture combines nearly every major category:

```text
Microcontroller
      +
Secure Element
      +
NFC
      +
OLED
      +
Buttons
      +
Encoder
      +
Battery
      +
USB
      +
Power Management
```

This makes the wallet a useful test case for the encyclopedia's future:

```text
Select Components
       ↓
Assign Pins
       ↓
Check Electrical Compatibility
       ↓
Generate Wiring
       ↓
Generate Firmware Configuration
       ↓
Simulate
       ↓
Build Hardware
       ↓
Test Hardware
```

---

# The Goal

The ultimate goal is not simply to document hardware.

It is to create a system where someone can go from:

```text
"I want to build this."
```

to:

```text
"What components do I need?"
        ↓
"What pins do I use?"
        ↓
"Are they electrically compatible?"
        ↓
"How should I wire them?"
        ↓
"What firmware do I need?"
        ↓
"Can I simulate it?"
        ↓
"What PCB should I build?"
        ↓
"How do I test it?"
```

with as little guesswork as possible.

---

# Contributing

When adding hardware, prioritize correctness over completeness.

A small, accurate component entry is more valuable than a huge entry containing guessed specifications.

When possible, include:

* official datasheet
* reference manual
* schematic
* manufacturer page
* exact module identification
* board revision
* verified pinout
* electrical specifications
* example wiring
* tested example code

If something is uncertain, mark it as uncertain.

---

# Status

This repository is actively expanding.

Current focus:

```text
┌────────────────────────────────────┐
│ Embedded Hardware Encyclopedia     │
├────────────────────────────────────┤
│                                    │
│ ✓ Microcontrollers                 │
│ ✓ Arduino                          │
│ ✓ ESP32                            │
│ ✓ Displays                         │
│ ✓ NFC / RFID                       │
│ ✓ Cameras                          │
│ ✓ Basic Virtual Lab                │
│                                    │
│ → Structured Hardware Database     │
│ → Wiring Engine                    │
│ → Compatibility Engine             │
│ → Virtual Hardware Expansion       │
│ → Hardware Wallet                  │
│                                    │
└────────────────────────────────────┘
```

---

# License

Add the project's chosen license here.

Hardware manufacturer documentation, datasheets, trademarks, and third-party reference material remain the property of their respective owners.

This repository should not imply endorsement by component manufacturers unless explicitly stated.

---

# Embedded Hardware Encyclopedia

**Document it. Wire it. Simulate it. Build it.**

```
```
