# 3-Button LED Control with Arduino

## Project Overview
This project demonstrates a simple **Arduino circuit with 3 pushbuttons and 3 LEDs**, where each button controls its corresponding LED independently. This project teaches beginners about:

- Reading digital inputs from buttons  
- Controlling digital outputs (LEDs)  
- Using **pull-down resistors** to prevent floating inputs  
- Wiring circuits on a breadboard  

---

## Components Needed

- 1 × Arduino Uno (or compatible board)  
- 3 × Pushbuttons  
- 3 × LEDs  
- 3 × 470Ω resistors (for LEDs)  
- 3 × 10kΩ resistors (for pull-downs)  
- Breadboard and jumper wires  

---

## Circuit Diagram

![Breadboard Diagram]()

> Replace the URL above with your actual image file in your repository.  

**LEDs:**

- Each LED has its **long leg (anode) → Arduino digital pin** (8, 9, 10) via 470Ω resistor.  
- Short leg (cathode) → GND.  

**Buttons (with pull-down resistors):**

- **One leg of the button → +5V**  
- **Opposite leg → Arduino input pin** (2, 4, 7) **and** connected to **GND through 10kΩ resistor**  
- This resistor ensures the pin reads LOW when the button is not pressed.  

> LEDs are **OFF by default**. Pressing a button turns its corresponding LED ON.

---

## Arduino Code

```cpp
// constants for pins:
const int buttonPin1 = 2;  
const int buttonPin2 = 3;  
const int buttonPin3 = 4;  

const int ledPin1 = 8;      
const int ledPin2 = 9;      
const int ledPin3 = 10;     

// variables for button states:
int buttonState1 = 0;  
int buttonState2 = 0;  
int buttonState3 = 0;  

void setup() {
  // initialize LED pins as outputs:
  pinMode(ledPin1, OUTPUT);
  pinMode(ledPin2, OUTPUT);
  pinMode(ledPin3, OUTPUT);

  // initialize button pins as inputs:
  pinMode(buttonPin1, INPUT);
  pinMode(buttonPin2, INPUT);
  pinMode(buttonPin3, INPUT);
}

void loop() {
  // read each pushbutton state:
  buttonState1 = digitalRead(buttonPin1);
  buttonState2 = digitalRead(buttonPin2);
  buttonState3 = digitalRead(buttonPin3);

  // control each LED independently:
  digitalWrite(ledPin1, (buttonState1 == HIGH) ? HIGH : LOW);
  digitalWrite(ledPin2, (buttonState2 == HIGH) ? HIGH : LOW);
  digitalWrite(ledPin3, (buttonState3 == HIGH) ? HIGH : LOW);
}
```
