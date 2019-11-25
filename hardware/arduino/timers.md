# Timers

Timers are handy in case you want to have things happen according to a certain timing in your code and you can't use **delay\(\)**. The delay function is easy to use, but also prevents your code from doing anything else at the same time. While it is waiting it won't check any sensors values or do anything else from your code.

You can build timers yourself by comparing the time your Arduino has been running with the last time you did a certain thing in your code, though this can be a lot of work, especially if you're trying to time multiple things.

The Chrono library is made to make this process very easy \(a library is a collection of code made to be included in your sketch and provide a certain functionality\). Go ahead and download the following link.

{% embed url="https://github.com/SofaPirate/Chrono/archive/master.zip" %}

Next up, inside your Arduino app click on the dropdown **Sketch  →** **Include Library → Add .ZIP Library...** Then select the ZIP file you've just downloaded.

After this you should be able to find Chrono in the examples. Give this piece of code a try to see timers in action with the same blink example we have in Arduino basics.

```cpp
/*
 This code will toggle pin 13 on and off every second (1000 ms).
 This should be the debug LED's pin. So the debug LED should
 blink every second.
 */

// INCLUDE CHRONO LIBRARY : http://github.com/SofaPirate/Chrono
#include <Chrono.h> 

// Set the led's pin
int ledPin =  13; 

//Create a variable to hold the led's state
int ledState = HIGH;

// Instanciate a Chrono object.
Chrono ledChrono; 

void setup()
{
  pinMode(ledPin,OUTPUT);
  digitalWrite(ledPin,ledState);
}

void loop()
{

  if (ledChrono.hasPassed(1000) ) { // returns true if it passed 1000 ms since it was started
    ledChrono.restart();  // restart the crono so that it triggers again later
    
    // toggle the stored state
    if (ledState==HIGH){
      ledState=LOW;
    } else {
      ledState=HIGH;
    }
    
    // write the state to the pin
    digitalWrite(ledPin,ledState);
  }
}

```

 

