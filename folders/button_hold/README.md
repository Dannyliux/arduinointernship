# Button Hold Mode  
In this project, the LED will only turn on while holding the button. The moment you let go, it will turn off. It's simple, but it's a great first look at how an Arduino is going to read input and control outputs in real time. 

### How the code works:
```cpp
int BUTTON_PIN = 2;
int LED_PIN = 3;
```
These two lines will give names to the pins we're using. Pin 2 is where the button is connected, and pin 3 is where the LED is connected. Using names such as ```BUTTON_PIN``` instead of just 2 will make the code easier to read for us and we will be able to change later with ease. 

```cpp
void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED_PIN, OUTPUT);
}
```
```setup()``` will run once when the Arduino turns on. Here is how each pin will be used:
- ```INPUT_PULLUP``` - the button pin will read the signals coming in. The ```PULLUP``` part keeps the pin at a HIGH state when the button isn't pressed, so readings are reliable. 
- ```OUTPUT``` - the LED pin will be sending signals out to either turn the LED on or off.

```cpp
void loop() {
  buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {
    digitalWrite(


