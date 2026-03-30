# Toggle Mode
In this project, we will be toggling the LED on and off with te button. Press once--it'll stay on. Press again--it'll turn off. Unlike the Button Hold Project, you don't have to hold anything.
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
- ```lastButtonState``` - what the button was doing in the previous loop```
- ```ledState``` - whether the LED is currently off or on, stores as either ```true``` or ```false```
