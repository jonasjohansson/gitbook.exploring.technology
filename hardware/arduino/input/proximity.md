# Proximity

### [Sharp Distance Sensor](https://www.adafruit.com/product/164) \(9x short distance, 3x long distance\)

{% tabs %}
{% tab title="Product" %}
![](https://cdn-shop.adafruit.com/970x728/164-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
| Sensor pin | Arduino pin |
| :--- | :--- |
| Black wire | GND |
| Red wire | 5V |
| Yellow/white wire | A3 |

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

{% tabs %}
{% tab title="Product" %}
![](https://cdn-shop.adafruit.com/970x728/172-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
| Sensor pin | Arduino pin |
| :--- | :--- |
| GND | GND |
| V+ | 5V |
| 3 | A0 |
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int distsensor = checkDistanceSensor();
  
  Serial.print(F("Sensor = ")); 
  Serial.println(distsensor);
  
  // add your code to use the distensor value here
}

int checkDistanceSensor() {
  int distsensor, i;
  long time;
  distsensor = 0;
  for (i = 0; i < 8; i++) {
    distsensor += analogRead(0);
    delay(50);
  }
  distsensor /= 8;
  return distsensor;
}

```
{% endtab %}
{% endtabs %}

### [Parallax Wide Angle PIR](https://www.adafruit.com/product/189) \(3x\)

{% tabs %}
{% tab title="Product" %}
![](https://cdn-shop.adafruit.com/970x728/189-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
| Sensor pin | Arduino pin |
| :--- | :--- |
| Black wire | GND |
| Red wire | 5V |
| Yellow/white wire | Digital in 2 |

![](../../../.gitbook/assets/image%20%285%29.png)
{% endtab %}

{% tab title="Code" %}
```cpp
/*
 * PIR sensor tester
 */
 
int ledPin = 13;                // choose the pin for the LED
int inputPin = 2;               // choose the input pin (for PIR sensor)
int pirState = LOW;             // we start, assuming no motion detected
int val = 0;                    // variable for reading the pin status
 
void setup() {
  pinMode(ledPin, OUTPUT);      // declare LED as output
  pinMode(inputPin, INPUT);     // declare sensor as input
 
  Serial.begin(9600);
}
 
void loop(){
  val = digitalRead(inputPin);  // read input value
  if (val == HIGH) {            // check if the input is HIGH
    digitalWrite(ledPin, HIGH);  // turn LED ON
    if (pirState == LOW) {
      // we have just turned on
      Serial.println("Motion detected!");
      // We only want to print on the output change, not state
      pirState = HIGH;
    }
  } else {
    digitalWrite(ledPin, LOW); // turn LED OFF
    if (pirState == HIGH){
      // we have just turned of
      Serial.println("Motion ended!");
      // We only want to print on the output change, not state
      pirState = LOW;
    }
  }
}
```
{% endtab %}
{% endtabs %}

