# Mio

Mio turns serial communication  as a trigger for key presses and MIDI communication. It relies on specific commands and values being sent from a device over a serial line. The command and value will then be parsed, leaving only the value.

{% embed url="https://jonasjohansson.itch.io/mio" %}

All key logic is handled on the device and sent via serial. The message should be written with a **$ dollar** sign followed by the key. MIDI commands are sent by default.

{% tabs %}
{% tab title=" Code" %}
```csharp
void setup() {
  Serial.begin(9600);
  pinMode(2, INPUT_PULLUP);
  pinMode(3, INPUT_PULLUP);
  pinMode(4, INPUT_PULLUP);
  pinMode(5, INPUT_PULLUP);
}

void loop() {
  int btn1 = digitalRead(2);
  int btn2 = digitalRead(3);
  int btn3 = digitalRead(4);
  int btn4 = digitalRead(5);

  if (btn1 == LOW) {
    Serial.println("$w");
  }

  if (btn2 == LOW) {
    Serial.println("$s");
  }

  if (btn3 == LOW) {
    Serial.println("$a");
  }

  if (btn4 == LOW) {
    Serial.println("$d");
  }
}
```
{% endtab %}

{% tab title="Schematic" %}
| Button Pin  | Arduino Pin |
| :--- | :--- |
| Button 1 \(orange wire\) | Digital 0 |
| Button 2 \(green wire\) | Digital 1 |
| Button 3 \(blue wire\) | Digital 2 |
| Button 4 \(purple wire\) | Digital 3 |

![](../.gitbook/assets/image%20%287%29.png)
{% endtab %}
{% endtabs %}

## Websockets

From version 1.1.1 Mio creates a local websocket server with the default port 8080 \(can be changed under Preferences\). This allows other systems \(pretty much anything\) that uses sockets, such as [Processing](../software/p5/), to pick up and act on the information. This means that generative graphics, for instance, can be manipulated by a Arduino. Messages sent should be made up of a string of alphabetical letters followed by the numerical value eg. `dist327`

{% tabs %}
{% tab title=" Arduino" %}
```csharp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(0);
  int rand = random(255);
  Serial.println("dist"+String(val));
  Serial.println("rand"+String(rand));
}
```
{% endtab %}

{% tab title="Processing" %}
```javascript
const socket = new WebSocket("ws://127.0.0.1:8080");

let bg = 220;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(bg);
}

socket.onmessage = data => {
  let dataObject = JSON.parse(data.data);
  print(dataObject);
  if (dataObject.id === "rand"){
    bg = dataObject.val;
  }
};
```
{% endtab %}
{% endtabs %}

It is possible to connect to the local websocket server from machines outside of the network using [ngrok](https://ngrok.com/docs). Forward the correct port and on the receiving end use the newly generated address. Now local information can be sent loball 

## Troubleshooting

### Unidentified Developer

Because Mio is made by an [Unidentified Developer](https://jonasjohansson.se/) the Control key must be pressed while clicking the app icon. Then choose **Open** from the menu.

### Permission

In order to control the keyboard Mio requires permissions. On Mac go to System preferences &gt; Security & Privacy, unlock the page by clicking the lock and providing the password, and then under Accessibility find Mio and tick the box. **If a new version has been installed, this might have to be done again by toggling the checkbox!**

![](../.gitbook/assets/permissions.png)

### Resource Busy

Mio can not be connected at the same time that any other device is listening to the serial communication, such as **Arduino's Monitor or Plotter**. The same is true for the other way around.

### Faster communication

It is possible to speed up the communication between the serial device and computer, by bumping up the **Baudrate** from **9600** to **115200**. This must be done within the code as well as in Mio. If you are running Arduino, remember to change it also in the monitor \(in the bottom right corner\).

![](../.gitbook/assets/serial.png)

