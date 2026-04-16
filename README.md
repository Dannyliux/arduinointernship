# Arduino LED & Button Workshop

An introductory Arduino workshop designed for students with no prior coding or electronics experience. Students will build a simple circuit and write code to control an LED using a push button — learning the fundamentals of input, output, and real-time hardware control.

**Workshop Duration:** ~2 Hours  
**Skill Level:** Complete Beginner  
**Projects:** 2 (Button Hold Mode & Toggle Mode)

---

## Learning Objectives

By the end of this workshop, students will be able to:

- Identify and connect basic electronic components (LED, push button, breadboard, jumper wires)
- Understand the difference between **input** and **output** on a microcontroller
- Read a button state using `digitalRead()`
- Control an LED using `digitalWrite()`
- Understand how `setup()` and `loop()` work in Arduino code
- Explain concepts like `INPUT_PULLUP` and debouncing in plain language

---

## Repository Structure

```
arduinointernship/
├── folders/
│   ├── button_hold/         → Project 1: Hold the button → LED turns on. Let go → LED turns off
│   └── toggle_mode/         → Project 2: Click the button → LED stays on. Click again → LED turns off
├── resources/
│   ├── diagrams/            → Wiring diagrams for Arduino Nano and Uno
│   └── images/              → Step-by-step setup photos
├── materials.md             → Full parts list per student station
├── lesson_plan.md           → Facilitator lesson plan (coming soon)
└── README.md                → You are here
```

---

## Projects

### Project 1 — Button Hold Mode
**Hold** the button → the LED lights up. **Let go** → the LED turns off. It responds in real time as long as you keep the button pressed. This project introduces `digitalRead()`, `digitalWrite()`, `INPUT_PULLUP`, and basic if/else logic.

📁 [View Button Hold](./folders/button_hold)

---

### Project 2 — Toggle Mode
**Click** the button once → the LED turns on and **stays on**. **Click again** → it turns off. No holding required — the LED remembers its state between button presses. This project builds on Project 1 by introducing state tracking, edge detection, and debouncing.

📁 [View Toggle Mode](./folders/toggle_mode)

---

## Materials

Each student station requires:

| Item | Quantity |
|------|----------|
| Arduino Nano or Uno | 1 |
| Push Button | 1 |
| LED (any color) | 1 |
| Breadboard | 1 |
| Jumper Wire Cables | 5 |
| Computer | 1 |
| USB Cable | 1 |

📄 [Full materials list with notes → materials.md](./materials.md)

---

## Getting Started (For Staff)

1. Review the [materials list](./materials.md) and set up each student station ahead of time
2. Make sure the Arduino IDE is installed on each computer
3. Follow the step-by-step wiring diagrams in [`resources/diagrams`](./resources/diagrams)
4. Start with **Project 1 (Button Hold)** before moving to Project 2
5. Use the lesson plan for timing and facilitation guidance *(coming soon)*

---

## Resources

- 📐 [Wiring Diagrams](./resources/diagrams)
- 🖼️ [Setup Images](./resources/images)
- 📋 [Materials List](./materials.md)
- 🗒️ Lesson Plan *(coming soon)*

---

*Developed as part of the Yo Soy STEM Arduino Workshop Series.*
