# Basics

| Parts | Quantity |
| :--- | :--- |
| Arduino Uno | 1 |
| Breadboard | 1 |
| LDR \(Photocell\) | 1 |
| LED \(any color\) | 3 |
| Button | 1 |
| Piezo | 1 |
| Potentiometer | 1 |
| Wire Male-to-Male \(any color\) | 5 |
| Resistor 10k | 2 |

### Special characters

Before writing code, make sure you can write the characters! Programming uses several special symbols that may feel alien, so we have a short list below which you can copy & paste from. To figure out how to type these, on Mac, turn on the [Keyboard Viewer](https://support.apple.com/en-euro/guide/mac-help/mchlp1015/mac)!

`/* ( ) { } [ ] | & / > < ; */`

### [Blink](https://www.arduino.cc/en/tutorial/blink)

{% tabs %}
{% tab title="Code" %}
```cpp
void setup() {
  pinMode(13, OUTPUT);
}

void loop() {
  digitalWrite(13, HIGH);
  delay(1000);
  digitalWrite(13, LOW);
  delay(1000);
}
```

* [ ] Change the LED blink speed using the delay function
* [ ] Create variables for the led pin number and delay amount
{% endtab %}

{% tab title="Solution" %}
```cpp
int ledPin = 13;
int wait = 500;

void setup() {
  pinMode(ledPin, OUTPUT);
}

void loop() {
  digitalWrite(ledPin, HIGH);
  delay(wait);
  digitalWrite(ledPin, LOW);
  delay(wait);
}
```
{% endtab %}
{% endtabs %}

### [Button](https://www.arduino.cc/en/tutorial/button)

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/button.png)
{% endtab %}

{% tab title="Code" %}
{% code title="" %}
```cpp
void setup() {
  pinMode(2, INPUT);
  Serial.begin(9600);
}

void loop() {
  int buttonState = digitalRead(2);
  Serial.println(buttonState);
}
```
{% endcode %}

* [ ] Use the Serial Monitor to read the state of the button
* [ ] Create a variable for the button pin
* [ ] Create your own button using your body
{% endtab %}
{% endtabs %}

### Blink + Button

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/blink-button%20%281%29.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  pinMode(2, INPUT);
  pinMode(13, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int buttonState = digitalRead(2);
  Serial.println(buttonState);

  if (buttonState == 1){
      digitalWrite(13, HIGH);
  } else {
      digitalWrite(13, LOW);
  }
}
```
{% endtab %}
{% endtabs %}

### [Fade](https://www.arduino.cc/en/tutorial/fade)

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/fade-2.png)
{% endtab %}

{% tab title="Code" %}
```cpp
int brightness = 0;
int fadeAmount = 5;

void setup() {
  pinMode(9, OUTPUT);
}

void loop() {
  analogWrite(9, brightness);
  brightness = brightness + fadeAmount;
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  delay(30);
}
```
{% endtab %}

{% tab title="Advanced" %}
```cpp
void setup() {
  pinMode(9, OUTPUT);
}

void loop() {
  float timer = millis()/1000.0;
  int brightness = 128 + 128 * sin(timer);
  analogWrite(9, brightness);
  delay(30);
}
```
{% endtab %}
{% endtabs %}

### [Potentiometer](https://www.arduino.cc/en/tutorial/potentiometer)

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/potentiometer.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(0);
  Serial.println(val);
}
```

* [ ] Create a variable for the potentiometer pin
* [ ] Use the Serial Monitor to read the value of the potentiometer
{% endtab %}
{% endtabs %}

### Fade + Potentiometer

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/fade-potentiometer.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(0);
  Serial.println(val);
  analogWrite(9, val/4); // 1024/4 = 256
}
```

* [ ] Add a second potentiometer and LED and get it control the LED brightness
{% endtab %}
{% endtabs %}

### [Photocell](https://learn.adafruit.com/photocells/arduino-code)

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/photo.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}
void loop() {
  int val = analogRead(0);
  Serial.println(val);
}
```

* [ ] Use the Serial Monitor to read the state of the photocell
{% endtab %}
{% endtabs %}

### Piezo

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/piezo.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
}

void loop() {
  tone(4, 255);
}
```
{% endtab %}
{% endtabs %}

### Photo resistor + Piezo

{% tabs %}
{% tab title="Schematic" %}
![](../../.gitbook/assets/photo-piezo.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(0);
  Serial.println(val);
  tone(4, val);
}
```

* [ ] Connect an LED and have the photocell control its brightness
* [ ] Find piezo melodies and play them!
{% endtab %}
{% endtabs %}

