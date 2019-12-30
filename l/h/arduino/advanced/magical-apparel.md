# Wearables

### Gemma

Gemma is a tiny micro-controller that works like an Arduino.

Learn more about the Gemma: [https://learn.adafruit.com/introducing-gemma/](https://learn.adafruit.com/introducing-gemma/)

#### Parts

* 1x Adafruit GEMMA
* 1x USB Micro Lipo Charger
* 1x NeoPixel Ring - 16 x WS2812 5050 RGB LED with Integrated Drivers

If Ring

* 1x NeoPixel Ring - 16 x WS2812 5050 RGB LED with Integrated Drivers
* 1x LiPo Battery 3.7V / 250mAh

If Stick

* 1x NeoPixel Stick - 8 x WS2812 RGB LED
* 1x Batteri LiPo 3.7V 110mAh

If Strip

* 1x Mini Skinny NeoPixel Digital RGB LED Strip - 60 LED/m \(Black PCB\) - 1m
* 1x LiPo Battery 3.7V / 250mAh

#### Step 1: Solder components

Solder wires between the copper plates on the Gemma and the Neopixels by following this guide: [https://learn.adafruit.com/gemma-hoop-earrings/solder-components](https://learn.adafruit.com/gemma-hoop-earrings/solder-components). This process still applies even if you are not working with the Neopixel Ring.

| Wire color | Gemma | Neopixel |
| :--- | :--- | :--- |
| White | IN \(Data Input\) | D0~ |
| Red | VCC \(Power 5V DC\) | Vout |
| Black | GND \(Power Signal Ground\) | GND |

**Pro tip:**

1. Solder wires to the Gemma first, and don't attempt to pre-calculate the length of wires. It's easer to add a bit extra and then shorten as the need presents itself.
2. Attach the wires to the back of the Gemma so
3. Do not push the wire through the hole of the Gemma, instead melt the solder on it as it rests on the copper plate.
4. The color of the wire does not have any importance, it only for convenience and by convention.

Learn more about soldering: [http://guide.exploring.technology/prototyping/soldering.md](http://guide.exploring.technology/prototyping/soldering.md)

#### Step 2: Programming

1. Download and install Arduino IDE, follow the guide here: [http://guide.exploring.technology/physical-computing/arduino/](http://guide.exploring.technology/physical-computing/arduino/)

#### Install the NeoPixel library

1. Open Arduino IDE
2. Sketch &gt; Include Library &gt; Manage Libraries
3. Search for "Adafruit NeoPixel", select the relevant package and click "install"

#### Upload code to the Gemma

Check that you have the correct setting in Arduino before trying to send the code to Gemma.

1. Tools &gt; Board and check that "Adafruit Gemma" is selected
2. Make sure Gemma is on by flipping the switch from OFF to ON.

#### Step 3: Connect power

