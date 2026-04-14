# Toggle Mode
In this project, we will be toggling the LED on and off with the button. Press once--it'll stay on. Press again--it'll turn off. Unlike the Button Hold Project, you don't have to hold anything.
The circuit wiring is exactly the same as before. Only the code changes. 

### How the code works:
Same as before, the set pin numbers for the button and LED are:
```cpp
int BUTTON_PIN = 2;
int LED_PIN = 3;
```
---

```cpp
int buttonState = 0;
int lastButtonState = HIGH;
bool ledState = false;
```

We have three variables instead of one. This is the key difference from Holding:
- ```buttonState``` - the reading fo the button right now.
- ```lastButtonState``` - what the button was doing in the previous loop
- ```ledState``` - whether the LED is currently off or on, stores as either ```true``` or ```false```
Remember the last state because toggling will only happen at the moment the button is pressed, not the entire time we hold it down.

--- 

```cpp
void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED_PIN, OUTPUT);
}
```
We will change nothing, the setup is the same as Hold button.

```cpp
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
In this, every cycle the loop will:
1. **Read** the current button state.
2. **Check** if the button went from not pressed to pressed. This is what ```lastButtonState == HIGH && buttonState == LOW``` is for.
3. **Flip** the LED state with ```!ledState```. If it was on originally, it will turn off, and vice versa.
4. **Write** the LED state to the pin
5. **Save** the current state as ```lastButtonState``` for the next cycle.
6. **Wait** 50ms to debounce

#### What is debouncing?
Physical buttons aren't making clean connections when pressed. They usually bounce quickly, which the Arduino can take in as many presses. So I used the delay(50) to smooth that out

#### What does !ledState do?
The ```!``` just means the "not" operator. It flips true and false statements to false and true. So everytime we press the button, the LED will switch to whatever state it _wasn't_ before.

---

### Customizing the Pins
If your wiring uses different pins, just update them at the top:
```cpp
int BUTTON_PIN = 2;  // change 2 to whatever pin your button is on
int LED_PIN = 3;     // change 3 to whatever pin your LED is on
```

