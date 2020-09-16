# Smoothing

When reading values from a sensor it can act "jumpy" or "noisy", which can be tricky when the output should appear smooth and stable.

The "input noise" can be improved by _smoothing_ the values. This means taking a certain amount of the most recent values, and then calculating their running average.

For instance, if the last 4 values were 101,102,103,104 and then suddenly there's a jump and the 5th value is **110**, then the average would be **104** \(520 divided by 5\).

![Blue is the raw sensor value while red is smoothed](../../../../.gitbook/assets/image%20%284%29.png)

To make matters simple, use a library!

1. Download [Smoothed library](https://github.com/MattFryer/Smoothed)
2. In Arduino go to **Sketch &gt; Include Library &gt; Add .ZIP Library...**  and select the zip folder
3. Restart Arduino and run the code below

Give this piece of code a try to see smoothing in action with a sensor or potentiometer.

```cpp
#include <Smoothed.h>

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



