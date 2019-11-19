# Proximity

### [Sharp Distance Sensor](https://www.adafruit.com/product/164) \(9x short distance, 3x long distance\)

{% tabs %}
{% tab title="Product" %}
![](https://cdn-shop.adafruit.com/970x728/164-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
![](../../../.gitbook/assets/ir-proximity.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(A3);
  // convert sensor reading into 0-255
  // change 0-600 to whatever fits your sensor
  int mappedVal = map(val,0,600,0,255);
  Serial.print(val);
  Serial.print("\t");
  Serial.println(val);
}
```
{% endtab %}
{% endtabs %}

### [Maxbotix Ultrasonic Rangefinder](https://www.adafruit.com/product/172) \(3x\)

![](https://cdn-shop.adafruit.com/970x728/172-00.jpg)

### [Parallax Wide Angle PIR](https://www.adafruit.com/product/189) \(3x\)

![](https://cdn-shop.adafruit.com/970x728/189-00.jpg)

### [Ultrasonic Range Sensor](https://www.sparkfun.com/products/15569) \(2x\)

{% tabs %}
{% tab title="Producst" %}


![](../../../.gitbook/assets/image.png)
{% endtab %}

{% tab title="Code" %}
```cpp
/*
  Ultraconic Range Sensor
  VCC to arduino 5v GND to arduino GND
  Echo to Arduino pin 13 Trig to Arduino pin 12
*/

#define trigPin 13
#define echoPin 12

void setup() {
  Serial.begin (9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {
  long distance = callSensor();

  if (distance >= 200 || distance <= 0) {
    Serial.println("Out of range");
  } else {
    Serial.print(distance);
    Serial.println(" cm");
  }
  delay(500);
}

long callSensor() {
  long duration, distance;
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = (duration / 2) / 29.1;
  return distance;
}
```
{% endtab %}
{% endtabs %}

