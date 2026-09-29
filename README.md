# Astable-Multivibrator


## 📌 Project Overview

This project demonstrates an **Astable Multivibrator circuit using the NE555P timer IC**.

An astable multivibrator continuously switches between HIGH and LOW states without requiring an external trigger. The output of the 555 timer produces a continuous square-wave signal, which is used to blink an LED.

The circuit is designed and documented using **KiCad**.

---

## 🔧 Components Used

| Component | Value |
|-----------|-------|
| NE555P Timer IC | 1 |
| R1 | 1 kΩ |
| R2 | 50 kΩ |
| R3 | 330 Ω |
| C1 | 0.1 µF |
| LED | 1 |
| 2-Pin Screw Terminal | 1 |
| PWR_FLAG | 2 |
| GND | As required |

---

## ⚡ Circuit Description

The NE555P is configured in **astable mode**.

The timing components **R1, R2, and C1** determine the frequency and duty cycle of the output waveform.

The output from **Pin 3 (OUT)** of the NE555P is connected to an LED through a **330 Ω current-limiting resistor**.

When the 555 output switches HIGH and LOW continuously, the LED turns ON and OFF, producing a blinking effect.

---

## 🔌 NE555P Pin Connections

| Pin | Name | Connection |
|-----|------|------------|
| 1 | GND | Ground |
| 2 | TRIG | Connected to Pin 6 and timing capacitor |
| 3 | OUT | R3 → LED → GND |
| 4 | RST | VCC |
| 5 | CONT | Not connected |
| 6 | THRES | Connected to Pin 2 |
| 7 | DISCH | Junction of R1 and R2 |
| 8 | VCC | Positive supply |

---

## 🔗 Circuit Connections

### Power Supply

- J1 Pin 1 → VCC
- J1 Pin 2 → GND
- PWR_FLAG is connected to the VCC net.
- PWR_FLAG is connected to the GND net.

### Timing Network

- R1 = 1 kΩ
- R2 = 50 kΩ
- C1 = 0.1 µF
- R1 is connected between VCC and Pin 7.
- R2 is connected between Pin 7 and the Pins 2/6 junction.
- C1 is connected between the Pins 2/6 junction and GND.

### Output

- Pin 3 (OUT) → R3 (330 Ω)
- R3 → LED
- LED → GND

---

## 📐 Working Principle

The NE555 timer operates as an astable multivibrator by repeatedly charging and discharging the capacitor.

### Charging

The capacitor charges through:

**R1 + R2**

When the capacitor voltage reaches approximately **2/3 VCC**, the threshold comparator changes state and the discharge transistor turns ON.

### Discharging

The capacitor discharges through:

**R2**

When the capacitor voltage falls to approximately **1/3 VCC**, the output changes state again and the discharge transistor turns OFF.

This charging and discharging process repeats continuously.

As a result, Pin 3 produces a continuous square-wave output.

---

## 🧮 Frequency Calculation

For a 555 timer in astable mode:

```text
f = 1.44 / ((R1 + 2R2) × C1)
