# Automatic-Room-Light-Controller-with-Bidirectional-Visitor-Counter
# 💡 Automatic Room Light Controller with Bidirectional Visitor Counter

This project implements an intelligent embedded system that **automatically controls room lighting** and **counts the number of people** entering and exiting a room using infrared sensors and a microcontroller. The light remains on as long as one or more persons are in the room and turns off when the room is empty.

---

## 📌 Features

- Bidirectional visitor counting
- Automatic light control using relay
- Real-time person count displayed on a 7-segment display
- Infrared (IR) based sensor system
- Microcontroller-driven logic (8051 compatible)

---

## 📐 Project Overview

- Uses two IR sensor pairs (TX/RX) to detect entry and exit.
- 8051-based microcontroller (AT89S52) processes the inputs.
- The room light is controlled via a relay circuit.
- People entering increase the count, and those exiting decrease it.
- Light turns ON when the count is greater than zero and OFF when the count reaches zero.
- Displays person count using two 7-segment displays.

---

## 🧰 Components Used

| Component               | Quantity |
|------------------------|----------|
| AT89S52 Microcontroller | 1        |
| TSOP1738 IR Sensors     | 2        |
| 7-Segment Display (LTS 542) | 2    |
| IC 555 Timer            | 1        |
| Voltage Regulator (LM7805) | 1     |
| Resistors, Capacitors   | Multiple |
| Relay Module            | 1        |
| Diodes (IN4148)         | As needed |
| Transistors (BC547, 2N2222) | As needed |
| Transformer (12-0-12)   | 1        |
| Crystal Oscillator      | 1        |
| Reset Button & Switches | As needed |
| Power Supply (5V & 12V) | 1        |

---

## ⚙️ Functional Description

### 🔹 Sensor Operation
- **IR Sensor 1 interrupted first**: Waits for Sensor 2. If triggered, it increments the count and switches ON the light (if it was off).
- **IR Sensor 2 interrupted first**: Waits for Sensor 1. If triggered, it decrements the count. If the count becomes zero, the light turns OFF.

### 🔹 Microcontroller Logic
- Monitors sensor signals through Port 1
- Controls relay on Port 2 to switch room light
- Drives 7-segment display via Port 0 and Port 2
- Uses Timer Interrupt for display refresh and input debounce

---

## 🔌 Circuit Blocks

- **IR Transmitter Circuit**: Generates modulated 38 kHz signal using 555 timer.
- **IR Receiver**: TSOP1738 sensors detect modulation break due to a person crossing the beam.
- **Relay Driver**: Transistor-based circuit toggles relay to control external appliances like lights.
- **Microcontroller**: AT89S52 handles logic, counting, display, and control.

---

## 📈 Project Flow

1. System powers on and initializes count to zero.
2. IR sensors detect entry/exit sequences.
3. Person counter is updated accordingly.
4. Light turns ON if count > 0; turns OFF when count == 0.
5. Count is displayed on a 2-digit 7-segment display.

---

## 🔄 Future Enhancements

- Add fan or AC control along with lights
- Integrate door automation via a second relay
- Enhance entry/exit detection to handle simultaneous movement
- Add EEPROM/SD card logging for audit trails

---

## ➕ Advantages

- Energy-efficient: lights switch off when room is empty
- Low-cost, reliable automation solution
- Simple IR-based sensing logic
- Easy to maintain and expand

---

## ➖ Limitations

- Cannot distinguish simultaneous entry/exit of two people
- Limited to single-entry/single-exit door setup

---

## 🧠 Applications

- Home automation
- Office and meeting rooms
- Libraries and laboratories
- Lecture halls and classrooms

---

## 📎 Program Details

Assembly code and circuit logic are included in the project files. It runs on 8051 assembly language and uses internal counters and timers to refresh the display and track movement. The refresh rate ensures smooth UI display and stable operation.

---

## 📂 File Structure
📁 auto-room-light/
├── circuit_diagram.pdf
├── main.asm # Assembly source code for AT89S52
├── schematic.png # IR + Relay driver + Display interface
├── README.md # Project documentation

---

## ✅ Getting Started

1. Flash the `.hex` or `.asm` file into AT89S52.
2. Build the circuit as per the schematic.
3. Provide 5V/12V regulated power supply.
4. Walk through the IR sensors to see the count and auto lighting in action.

---

