---
description: All about buttons!
---

# Button

![](../../../.gitbook/assets/image%20%287%29.png)

Buttons come in about a million different shapes and sizes, and there is about a million things you can do with them! The most important thing to know is that most buttons in the end work about the same way and also don't require any special programming, Arduino likes them all the same :-\)

See the [Arduino Basics](../basics.md#button) page for a detailed explanation of hooking up a button.

If you're interested in knowing more about what you can do with buttons, try looking up the following types:

* Pushbutton \(momentary\)
* Toggle
* Switch
* Potentiometer \(not exactly a button, but can be used as one\)
* Rotary encoder
* Capacitive touch



### [Adafruit Toggle Capacitive Touch](https://learn.adafruit.com/adafruit-capacitive-touch-sensor-breakouts) \(2x\)

{% tabs %}
{% tab title="Product" %}
![](../../../.gitbook/assets/image%20%282%29.png)

See [Arduino Basics](../basics.md#button) for instruction
{% endtab %}

{% tab title="Schematic" %}
| Product pin | Arduino pin |
| :--- | :--- |
| VDD | 5V |
| GND | GND |
| OUT | Digital in 2 |
{% endtab %}

{% tab title="Code" %}
```cpp
const int buttonPin = 2;     // the number of the pushbutton pin
const int ledPin =  13;      // the number of the LED pin


int buttonState = 0;         // variable for reading the pushbutton status

void setup() {
  pinMode(ledPin, OUTPUT);      
  pinMode(buttonPin, INPUT);     
}

void loop(){
  buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {
    digitalWrite(ledPin, HIGH);  
  } else {
    digitalWrite(ledPin, LOW); 
  }
}
```
{% endtab %}
{% endtabs %}





### Resources

* [https://learn.sparkfun.com/tutorials/switch-basics/all](https://learn.sparkfun.com/tutorials/switch-basics/all)

