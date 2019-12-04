# Arduino

### Arduino on the forum

{% embed url="https://forum.exploring.technology/c/arduino" %}



Arduino is a brand of open-source electronics platform, based on easy-to-use hardware and software. Arduino boards can read inputs: light on a sensor, a finger on a button, or a Twitter message, and turn it into an output: activating a motor, turning on an LED or publishing something online. You can tell your board what to do by sending a set of instructions \(the code\). 

![](../../.gitbook/assets/dl_elx5_arduino_uno_v1.1_white-reduced.png)

Arduino comes in many shapes with various purposes, and other brands exist as well. However, the traditional Arduino Uno is a staple in education, and useful even though it's been around since 2005.

### Install

Begin by installing the Arduino IDE \(Integrated Development Environment\)  application:

* [MacOSX](https://www.arduino.cc/en/Guide/MacOSX)
* [Windows](https://www.arduino.cc/en/Guide/Windows)

{% hint style="danger" %}
macOS Catalina does not support Arduino, so refrain from updating if you wish to use this software!
{% endhint %}

When ready, open the app and find a new window, named with the current date, containing some basic code.

> Before we continue further, go to Preferences under Arduino &gt; Preferences and tick "Display line numbers" and "Enable code folding".

A document in Arduino is called a **sketch**, and the default example includes the following:

```javascript
void setup() {
}

void loop() {
}
```

Both **setup** and **loop** are **functions**. We use functions as a way to recycle code; without them, we would have to repeat our instructions. By use of functions, we can write complex code, include it in our function, and then "call it".

In the setup and loop case, these are pre-made by Arduino and have a default behaviour where setup is called once and happens before the loop, while loop is being called continuously - in a loop. _It is also possible to write our own functions._

### Connect

Connect the Arduino Uno with an A-B USB cable. The USB connection is necessary to program the board and not just to power it up. The Uno automatically draw power from either the USB or an external power supply. When connected, the green power LED \(labelled PWR\) should go on.

### Upload

Before uploading the sketch, make sure the correct items are selected under Tools &gt; Board and Tools &gt; Port. On the Mac, the serial port is probably something like /dev/tty.usbmodem241.

{% hint style="danger" %}
If you have a USB adapter for your laptop eg. Macbook then each time you plug in the Arduino you must reselect the serial port!
{% endhint %}

With everything set click the Upload button \(right arrow symbol\) or ⌘+U. When uploading the orange transmission LED \(labelled TX\) should flicker.

Congratulations! The Arduino should now be successfully connected to the computer, and the first piece of code is uploaded.

## Parts

There are some essential pieces required for most prototyping, and it is wise to get a solid understanding of their purpose from the start!

### Breadboard

A breadboard is a way of constructing electronics without having to use a soldering iron. Components are pushed into the sockets on the breadboard and then extra 'jumper' wires are used to make connections.

![](https://cdn-learn.adafruit.com/assets/assets/000/002/603/medium800/learn_arduino_breadboard_back_in_bits.jpg?1396784983)

The middle section of the board has two columns, each with 30 strips of connector, like the one pulled out and to the side of the breadboard. These connect together anything that is pushed through from the front into one of those five holes.

On either edge of the board are much longer sections of clip that join together the columns of holes marked by the blue and red lines on the front of the breadboard. These are generally used for GND \(blue\) and 5V \(red\).

* [https://learn.adafruit.com/breadboards-for-beginners](https://learn.adafruit.com/breadboards-for-beginners)
* [https://learn.sparkfun.com/tutorials/how-to-use-a-breadboard](https://learn.sparkfun.com/tutorials/how-to-use-a-breadboard)
* [Collin's Lab: Breadboards](https://www.youtube.com/watch?v=w0c3t0fJhXU)

### Wires

There are lots of little connections inside of your breadboard but they only go along in rows, basically making each pin or wire of a part have 5 total connection points. To wire up the parts you'll need to, um, wire the parts...with wire!

* [https://learn.adafruit.com/wires-and-connections](https://learn.adafruit.com/wires-and-connections)
* [https://learn.sparkfun.com/tutorials/working-with-wire](https://learn.sparkfun.com/tutorials/working-with-wire)

{% hint style="info" %}
Wires come in different colors, and some colors are standardises for certain type of connections; **black** is ground aka. minus- or GND and **red** is voltage aka. plus+ or 
{% endhint %}

