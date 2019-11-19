# Code

### Special characters

Before writing code, make sure you can write the characters! Programming uses several special symbols that may feel alien, so we have a short list below which you can copy & paste from. To figure out how to type these, on Mac, turn on the [Keyboard Viewer](https://support.apple.com/en-euro/guide/mac-help/mchlp1015/mac)!

`/* ( ) { } [ ] | & / > < ; */`

### Curly brackets {}

### void

"void" is written before

### Setup

Setup is a mandatory function that must exist before the Loop function. Setup is the first function to run and is only run once.

### Loop

Loop is a mandatory function that must exist _after_ the Setup function. Loop happens over and over again with a speed decided by the processing power of the Arduino.

### Square brackets \[\]

### Debug

To help debug our code we use the _Serial monitor_ and the _Serial plotter_.

We can tell our Arduino to send information about what is happening in the code. We do this using "serial communication" and by typing Serial.begin\(9600\) in the Setup function. 9600 is the baudrate, the speed which the computer and the Arduino communicates, and 9600 is the standard rate.

To print information type `Serial.println()` and within the parentheses you can print out variables, strings, numbers and more.

```csharp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int buttonState = digitalRead(2);
  if (buttonState == 1){
    Serial.println("button is pressed!");
  } else {
    Serial.println("button is released!")
  }
}
```

### PinMode

[https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/](https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/)

### analogWrite

[https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/](https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/)

### digitalWrite

[https://www.arduino.cc/reference/en/language/functions/digital-io/digitalwrite/](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalwrite/)

### analogRead

[https://www.arduino.cc/en/Tutorial/AnalogReadSerial](https://www.arduino.cc/en/Tutorial/AnalogReadSerial)

### digitalRead

[https://www.arduino.cc/en/Tutorial/DigitalReadSerial](https://www.arduino.cc/en/Tutorial/DigitalReadSerial)

### delay

[https://www.arduino.cc/reference/en/language/functions/time/delay/](https://www.arduino.cc/reference/en/language/functions/time/delay/)

### High / Low

### Millis

{% embed url="https://www.arduino.cc/en/Tutorial/BlinkWithoutDelay" %}

{% hint style="info" %}
Pro tip: you can right click on any word in the Arduino app and select View Reference to be taken to a page which explains about that function or variable.
{% endhint %}

### Analog inputs

### Analog outputs

### Breadboard

Refer to gitbook

### Jumper wires

Refer to gitbook

