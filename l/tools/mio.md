# Mio

Mio is a minimal input and output application that enables serial communication for computer interaction. There are other applications that can be useful to check out as well, such as the [Ableton Connection Kit](https://www.ableton.com/en/packs/connection-kit/).

### Install

Begin by [installing the Mio app](https://jonasjohansson.itch.io/mio). It is only available for Mac but the [source is open](https://github.com/jonasjohansson/mio) so it can be built for other platforms \(requires Electron and Node knowledge\).

### Connect

Run Mio and a small window will appear. **Refresh** to get an updated list of all the devices connected via serial. Select the intended device and click **Connect**. The default speed of communication is **9600** baud, but this can be changed to match the device speed. That's it! Mio is now listening to the messages sent by the device.

### Commands

All logic is handled on the sending device and made possible by printing specific messages.

| Example | Description | Version |
| :--- | :--- | :--- |
| $w | Press key \([available keys](https://robotjs.io/docs/syntax#keys)\) | 1.0.0 |
| !w | Release key | 1.1.6 |
| $mouse | Click mouse | 1.1.3 |
| 100,200 | Move cursor position. Any number, comma separated. | 1.1.3 |
| /composition/master0.1 | Send value to address. Any float. | 1.1.4 |
| r255 | Send id and val. Any name and number. | 1.1.1 |

{% hint style="success" %}
When sending a string and integer to Arduino only the first character will be used eg. red255 will become r255.
{% endhint %}

{% tabs %}
{% tab title=" Send" %}
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
    // press 'w' key
    Serial.println("$w");
  }

  if (btn2 == LOW) {
    // send 0.1 to an OSC address
    Serial.println("/composition/master0.1");
  }

  if (btn3 == LOW) {
    // move cursor to x 100 and y 200
    Serial.println("100,200");
  }

  if (btn4 == LOW) {
    int red = random(255);
    // send 'red' and a random value over sockets
    Serial.println("red" + String(red));
  }
}
```
{% endtab %}

{% tab title="Receive" %}
```csharp
int x, y;

void setup() {
  Serial.begin(9600);
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  // call mio first so variables are updated
  mio();
  digitalWrite(LED_BUILTIN, x);
}

void mio(){
  if (Serial.available() > 0) {
    char command = Serial.read();
    switch (command) {
      case 'x':
        x = Serial.parseInt();
        break;
      case 'y':
        y = Serial.parseInt();
        break;
    }
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

![](../../.gitbook/assets/image%20%287%29.png)
{% endtab %}

{% tab title="P5" %}
```javascript
let ws = new WebSocket("ws://127.0.0.1:8080");

let red = 0;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(red, 0, 0);
}

ws.onmessage = data => {
  let d = JSON.parse(data.data);
  print(d);
  if (d.id === "r") {
    red = d.msg;
  }
};
```
{% endtab %}

{% tab title="HTML" %}
```markup
<html>
  <body>
    <script>
      let ws = new WebSocket("ws://127.0.0.1:8080");
      ws.onopen = e => {
        var state = 0;
        setInterval(function(){
          state = (state === 0) ? 1 : 0
          ws.send("x"+state);
        },2000);
      }
      ws.onmessage = data => {
        let d = JSON.parse(data.data);
        console.log(d);
        if (d.id === "r") {
          document.documentElement.style.backgroundColor = `rgb(${d.msg},0,0)`;
        }
      };
    </script>
  </body>
</html>
```
{% endtab %}
{% endtabs %}

### Protocols

#### MIDI

MIDI commands are sent automatically with the control value being the index of the key in lookup table \(found in File &gt; Preferences\). 

#### OSC

OSC commands are sent by default on port 7001.

#### Websockets

Mio creates a local server through port 8080 making all commands available from any website. It is possible to connect to the local socket server from machines outside of the network using [ngrok](https://ngrok.com/docs). Forward the correct port and on the receiving end use the newly generated address. Another alternative is setting up a [server](https://glitch.com/~mio-server) and [client](https://glitch.com/~mio-client) on Glitch.

## Troubleshooting

### Unidentified Developer

Because Mio is made by an [Unidentified Developer](https://jonasjohansson.se/) the Control key must be pressed while clicking the app icon. Then choose **Open** from the menu.

### Permission

In order to control the keyboard, Mio requires permissions. On Mac, go to System preferences &gt; Security & Privacy, unlock the page by clicking the lock and providing the password, and then under Accessibility find Mio and tick the box. **If a new version has been installed, this must be done again by toggling the checkbox!**

![](../../.gitbook/assets/permissions.png)

### Resource Busy

Mio can not be connected at the same time that any other device is listening to the serial communication, such as **Arduino Monitor or Plotter**. The same is true for the other way around.

### Faster communication

It is possible to speed up the communication between the serial device and computer, by bumping up the **Baudrate** from **9600** to **115200**. This must be done within the code as well as in Mio. If you are running Arduino, remember to change it also in the monitor \(in the bottom right corner\).

![](../../.gitbook/assets/serial.png)

### No Communication

No response is likely due to Mio is minimised, not visible on the screen or another app is in fullscreen. If any of this occurs the app enters passive mode and can no longer detect keys being released. If a projector or second screen is in use, simply make sure is is visible on either one. Version 1.1.6 re-introduced the exclamation mark which will force a key to be released.

{% hint style="success" %}
A neat trick is to turn on the zoom feature and zoom in on an app to make it appear fullscreen.
{% endhint %}

### Window Invisible

If the window disappeared, go to Help &gt; Reset to restore all settings to normal.

