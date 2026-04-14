# Lesson Plan — Arduino LED & Button Workshop

**Program:** Yo Soy STEM
**Duration:** 2 Hours
**Audience:** Students with no prior coding or electronics experience
**Projects Covered:** Button Hold Mode & Toggle Mode
**Prepared by:** Danny

---

## Overview

In this workshop, students will be introduced to the Arduino Nano microcontroller. They will learn how to wire a simple circuit using an LED and a push button, and write code to control the LED in two different ways. No experience with coding or electronics is required — everything will be explained from scratch.

---

## Learning Objectives

By the end of this workshop, students will be able to:

- Identify basic electronic components (Arduino Nano, LED, push button, jumper wires)
- Wire a simple circuit on a breadboard
- Understand the difference between **input** and **output** on a microcontroller
- Read a button state using `digitalRead()`
- Control an LED using `digitalWrite()`
- Understand how `setup()` and `loop()` work in Arduino code
- Explain what `INPUT_PULLUP` and debouncing mean

---

## Materials Needed

See [materials.md](./materials.md) for the full list. Per station:

| Item | Quantity |
|------|----------|
| Arduino Nano | 1 |
| Push Button | 1 |
| LED (any color) | 1 |
| Jumper Wire Cables | 5 |
| Computer | 1 |
| USB Cable (Micro or Mini USB) | 1 |

---

## Pre-Workshop Checklist (For Staff)

Before students arrive, make sure:

- [ ] Arduino IDE is installed on every computer (see setup instructions below)
- [ ] CH340 USB driver is installed on Windows machines
- [ ] Each Arduino Nano has been tested with a blink sketch
- [ ] All USB cables support data transfer (not charge-only)
- [ ] Each station has all components laid out and ready
- [ ] Wiring diagrams are printed or displayed on screen

---

## Workshop Timeline

| Time | Section |
|------|---------|
| 0:00 – 0:15 | Part 1 — Setting Up the Arduino IDE |
| 0:15 – 0:30 | Part 2 — Introduction to Arduino & Electronics |
| 0:30 – 0:50 | Part 3 — Wiring the Circuit |
| 0:50 – 1:15 | Part 4 — Project 1: Button Hold Mode |
| 1:15 – 1:20 | Break |
| 1:20 – 1:45 | Part 5 — Project 2: Toggle Mode |
| 1:45 – 2:00 | Part 6 — Wrap Up & Challenges |

---

## Part 1 — Setting Up the Arduino IDE (15 min)

### What is the Arduino IDE?
The Arduino IDE (Integrated Development Environment) is the free software we use to write code and send it to the Arduino. Think of it like a translator — you write instructions in a language called C++, and the IDE sends those instructions to the hardware.

### Installation Steps

1. Go to [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
2. Download the version for your operating system (Windows, Mac, or Linux)
3. Run the installer and follow the on-screen instructions
4. Open the Arduino IDE once installed

### Installing the CH340 Driver (Windows only)
Some Arduino Nano boards use a CH340 chip for USB communication. If Windows does not recognize the board:

1. Download the CH340 driver from [https://sparks.gogo.co.nz/ch340.html](https://sparks.gogo.co.nz/ch340.html)
2. Run the installer
3. Restart the computer if prompted

### Connecting the Arduino Nano

1. Plug the Arduino Nano into the computer using the USB cable
2. Open the Arduino IDE
3. Go to **Tools → Board** and select **Arduino Nano**
4. Go to **Tools → Processor** and select **ATmega328P (Old Bootloader)** *(try this if uploads fail)*
5. Go to **Tools → Port** and select the port that shows your Arduino (usually `COM3` on Windows or `/dev/cu.usbserial` on Mac)

### Quick Test — Blink Sketch
Let's make sure everything is working before we start:

1. In the Arduino IDE, go to **File → Examples → 01.Basics → Blink**
2. Click the **Upload** button (right arrow icon)
3. If the built-in LED on the Nano starts blinking — success! Everything is connected correctly.

---

## Part 2 — Introduction to Arduino & Electronics (15 min)

### What is an Arduino?
An Arduino is a small computer that can read inputs (like a button being pressed) and control outputs (like turning on an LED). Unlike a regular computer, it runs one program over and over again, making it perfect for physical projects.

### Key Components

- **Arduino Nano** — The brain. It reads inputs and controls outputs based on your code.
- **LED** — Light Emitting Diode. It lights up when electricity flows through it in the correct direction. The **longer leg is positive (+)**.
- **Push Button** — A switch. When pressed, it completes a circuit and sends a signal to the Arduino.
- **Jumper Wires** — Cables used to connect components together.
- **USB Cable** — Powers the Arduino and lets us upload code from the computer.

### How Arduino Code is Structured
Every Arduino program (called a **sketch**) has two required sections:

```cpp
void setup() {
  // Runs ONCE when the Arduino turns on
  // Used to configure pins as input or output
}

void loop() {
  // Runs OVER AND OVER FOREVER
  // This is where the main logic lives
}
```

### Inputs and Outputs (Pins)
The holes along the sides of the Arduino Nano are called **pins**. Each pin can be configured as either:

- **INPUT** — The pin reads a signal coming in (e.g., a button press)
- **OUTPUT** — The pin sends a signal out (e.g., turning on an LED)

---

## Part 3 — Wiring the Circuit (20 min)

Both projects use the exact same circuit. Students only wire it once.

### Components to connect:
- LED connected to **Pin 3**
- Push button connected to **Pin 2** (the other leg connects to GND)
- All grounds connected to the GND pin on the Nano

> 📐 Refer to the wiring diagrams in [`resources/diagrams`](./resources/diagrams) for visual step-by-step instructions.

### Important reminders:
- The **longer leg of the LED is positive (+)** — it must face the correct direction or it won't light up
- Double-check all connections before plugging in the USB cable
- If the LED doesn't light up, try flipping it

---

## Part 4 — Project 1: Button Hold Mode (25 min)

### Concept
When you **hold** the button, the LED turns on. When you **let go**, it turns off. The LED only stays on as long as you keep the button pressed.

### The Code

```cpp
int BUTTON_PIN = 2;
int LED_PIN = 3;
int buttonState = 0;

void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {
    digitalWrite(LED_PIN, LOW);
  } else {
    digitalWrite(LED_PIN, HIGH);
  }
}
```

### Code Walkthrough

- `int BUTTON_PIN = 2` — We give pin 2 a name so the code is easier to read
- `INPUT_PULLUP` — Configures the button pin with an internal pull-up resistor. This keeps the pin at HIGH when the button isn't pressed, so readings are stable
- `digitalRead(BUTTON_PIN)` — Reads whether the button is pressed or not
- `digitalWrite(LED_PIN, HIGH/LOW)` — Turns the LED on or off
- **Why is LOW = pressed?** Because `INPUT_PULLUP` keeps the pin HIGH by default. When you press the button, it connects the pin to ground and pulls it LOW

### Steps for Students
1. Open the Arduino IDE
2. Type in (or copy) the code above into a new sketch
3. Click **Upload**
4. Press and hold the button — the LED should turn on
5. Let go — the LED should turn off

---

## Part 5 — Project 2: Toggle Mode (25 min)

### Concept
**Click** the button once → the LED turns on and **stays on**. **Click again** → it turns off. The circuit is exactly the same as Project 1 — only the code changes.

### The Code

```cpp
int BUTTON_PIN = 2;
int LED_PIN = 3;
int buttonState = 0;
int lastButtonState = HIGH;
bool ledState = false;

void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  buttonState = digitalRead(BUTTON_PIN);

  if (lastButtonState == HIGH && buttonState == LOW) {
    ledState = !ledState;
  }

  digitalWrite(LED_PIN, ledState);
  lastButtonState = buttonState;
  delay(50);
}
```

### Code Walkthrough

- `lastButtonState` — Remembers what the button was doing in the previous loop cycle
- `bool ledState` — Tracks whether the LED is currently on or off (true/false)
- `lastButtonState == HIGH && buttonState == LOW` — Detects the exact **moment** the button is pressed (transition from not-pressed to pressed), not the entire time it's held
- `!ledState` — The `!` means "not". It flips the LED state: if it was on, it turns off; if it was off, it turns on
- `delay(50)` — Waits 50 milliseconds to debounce the button

### What is Debouncing?
Physical buttons don't make a perfectly clean connection when pressed — they "bounce" and can register multiple presses in a split second. Adding a short `delay(50)` smooths this out so the Arduino only registers one press per click.

### Steps for Students
1. Keep the same circuit wired from Project 1
2. Open a new sketch in the Arduino IDE (**File → New**)
3. Type in (or copy) the code above
4. Click **Upload**
5. Click the button once — the LED should turn on and stay on
6. Click again — it should turn off

---

## Part 6 — Wrap Up & Challenges (20 min)

### Review Questions
Ask students to explain in their own words:

- What is the difference between `setup()` and `loop()`?
- What does `INPUT_PULLUP` do?
- Why does LOW mean the button is pressed?
- What is debouncing and why does it matter?

### Challenge Ideas (for students who finish early)
- Can you change the LED pin to a different number and update the code to match?
- Can you make the LED blink instead of staying on solid in Toggle Mode?
- Can you add a second LED and make them take turns?

### Closing
Thank students for participating. Remind them that everything they built today — reading inputs and controlling outputs — is the foundation of almost all electronics projects, from robots to smart home devices.

---

## Troubleshooting Guide

| Problem | Possible Cause | Solution |
|---------|----------------|----------|
| LED doesn't light up | LED is backwards | Flip the LED so the longer leg faces the correct direction |
| Arduino not recognized by computer | Missing CH340 driver | Install the CH340 driver (Windows) |
| Upload fails | Wrong board or port selected | Check Tools → Board and Tools → Port |
| Upload fails | Old bootloader | Go to Tools → Processor → ATmega328P (Old Bootloader) |
| LED lights up when button is NOT pressed | Code logic inverted | Remember: LOW = pressed with INPUT_PULLUP |
| Button doesn't seem to register | Loose wiring | Check all connections |
| LED stays on constantly | Button wired incorrectly | Refer to the wiring diagram |

---

## Additional Resources

- 📐 [Wiring Diagrams](./resources/diagrams)
- 🖼️ [Setup Photos](./resources/images)
- 📋 [Materials List](./materials.md)
- 🔗 Arduino IDE Download: [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
- 🔗 Arduino Reference: [https://www.arduino.cc/reference/en/](https://www.arduino.cc/reference/en/)
