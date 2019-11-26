# Smoothing

![Preview of the Arduino Serial Plotter \(blue is raw values, red is smoothed\)](../../../.gitbook/assets/image%20%282%29.png)

Sometimes you may find that the values you're getting from your sensor, or some other kind of input are not as consistent as you would like. This is called input noise, and can be improved by smoothing the values. What this means is that it takes a certain amount of recent values \(for instance the last ten\) and then calculates the average over that amount of values.

{% embed url="https://github.com/MattFryer/Smoothed/archive/v1.1.zip" %}

Next up, inside your Arduino app click on the dropdown **Sketch  →** **Include Library → Add .ZIP Library...** Then select the ZIP file you've just downloaded.

After this you should be able to find Smoothed in the examples. Give this piece of code a try to see smoothing in action with a sensor or potentiometer.

```cpp
/*
 Sensor Input Smoothing
 Demonstrates smoothing of a sensor input via various methods.


 Created by Matthew Fryer, edited for simplicity by Mickey van Olst

 This example code is in the public domain.

 */

#include <Smoothed.h> 	// Include the library

// Create two instances of the class to use. 
Smoothed <float> mySensor;

void setup() {
	Serial.begin(9600);

	// Initialise the first sensor value store. We want this to be the simple average of the last 10 values.
	// Note: The more values you store, the more memory will be used.
	mySensor.begin(10);
}

void loop() {
    // Read the value from the sensor
    float currentSensorValue = analogRead(A0);
    
    // Add the new value to both sensor value stores
    mySensor.add(currentSensorValue);
    
    // Get the smoothed values
    float smoothedSensorValueAvg = mySensor.get();
    
    // Output the smoothed values to the serial stream. Open the Arduino IDE Serial plotter to see the effects of the smoothing methods.
    Serial.print(currentSensorValue); 
    Serial.print("\t"); 
    Serial.println(smoothedSensorValueAvg);

    delay(10);
}
```



