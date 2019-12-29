# Timers

The delay function is easy to use but prevents Arduino from doing anything else at the same time, for instance reading a sensor value. For these situations use a timer!

You can build timers yourself by comparing the time your Arduino has been running with the last time you did a certain thing in your code, though this can be a lot of work, especially if you're trying to time multiple things. Luckily, there's a library we can use to make this process easy!

1. Download the [Chrono library](https://github.com/SofaPirate/Chrono/archive/master.zip)
2. In Arduino go to **Sketch  →** **Include Library → Add .ZIP Library...**  and select the zip folder
3. Restart Arduino and run the code below

```cpp
#include <Chrono.h>

Chrono ledChrono;

int ledState = LOW;

void setup() {
  pinMode(13, OUTPUT);
}

void loop() {

  // returns true if it passed 1000 ms since it was started
  if (ledChrono.hasPassed(1000) ) {
   // restart the crono so that it triggers again later 
    ledChrono.restart();

    if (ledState == HIGH) {
      ledState = LOW;
    } else {
      ledState = HIGH;
    }

    digitalWrite(ledPin, ledState);
  }
}
```

 

