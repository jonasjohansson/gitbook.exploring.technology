# Wireless

Going wireless is a bold move, and fun! There are several ways, but using Wifi is one of the most rewarding ones, since it opens up to so many other possibilities.

It is by no means trivial but 

```cpp
#include <WiFi101.h>
#include <WiFiClient.h>
#include <WiFiServer.h>
#include <WiFiSSLClient.h>
#include <WiFiUdp.h>
#include <SPI.h>
#include <WiFi101.h>

// Network SSID (name)
char ssid[] = "";

// Network password
char pass[] = "";

// LED
int ledPin = 5;

String readString;

int status = WL_IDLE_STATUS;
WiFiServer server(80);

void setup() {
  Serial.begin(9600);
  Serial.print("Start communication");

  // Attach LED to pin
  pinMode(ledPin, OUTPUT);

  // Check for the presence of the shield
  Serial.print("WiFi101 shield: ");
  if (WiFi.status() == WL_NO_SHIELD) {
    Serial.println("NOT PRESENT");

    return; // Don't continue
  }

  Serial.println("DETECTED");

  // Attempt to connect to Wifi network:
  while ( status != WL_CONNECTED) {
    // Turn off LED
    digitalWrite(ledPin, LOW);
    
    Serial.print("Attempting to connect to Network named: ");

    // Print the network name (SSID)
    Serial.println(ssid);

    // Connect to WPA/WPA2 network. Change this line if using open or WEP network:
    status = WiFi.begin(ssid, pass);

    // Wait 5 seconds for connection:
    delay(5000);
  }

  // Start the web server on port 80
  server.begin();

  // You're connected now, so print out the status
  printWifiStatus();

  // Turn on LED
  digitalWrite(ledPin, HIGH);
}

void loop() {
  // listen for incoming clients
  WiFiClient client = server.available();

  // If you get a client,
  if (client) {

    // Make a String to hold incoming data from the client
    String currentLine = "";

    // Loop while the client's connected
    while (client.connected()) {

      // If there's bytes to read from the client
      if (client.available()) {

        // Read a byte
        char c = client.read();

        // Print it out the serial monitor
        Serial.write(c);

        // If the byte is a newline character
        if (c == '\n') {

          // If the current line is blank, you got two newline characters in a row.
          // that's the end of the client HTTP request, so send a response:
          if (currentLine.length() == 0) {

            // Create interface
            createInterface(client);

            // Break out of the while loop:
            break;
          }
          else {      // If you got a newline, then clear currentLine:
            currentLine = "";
          }
        } else if (c != '\r') {  // If you got anything else but a carriage return character,
          currentLine += c;      // add it to the end of the currentLine
        }

        ///////////////////////////////////////////////////////////////////
        //                           RECEIVE                             //
        ///////////////////////////////////////////////////////////////////

        if (currentLine.endsWith("GET /HIGH")) {
          // Do stuff here
          digitalWrite(ledPin, HIGH);

          // Give the server some time to read the response
          delay(100);
          
          client.stop();
        }

        if (currentLine.endsWith("GET /LOW")) {
          // Do stuff here
          digitalWrite(ledPin, LOW);

          // Give the server some time to read the response
          delay(100);

          client.stop();
        }
      }
    }

    // Close the connection
    client.stop();
  }
}

///////////////////////////////////////////////////////////////////
//                       WIFI INFORMATION                        //
///////////////////////////////////////////////////////////////////

void printWifiStatus() {
  // Print the SSID of the network you're attached to:
  Serial.print("SSID: ");
  Serial.println(WiFi.SSID());

  // Print your WiFi shield's IP address:
  IPAddress ip = WiFi.localIP();
  Serial.print("IP Address: ");
  Serial.println(ip);

  // Print the received signal strength:
  long rssi = WiFi.RSSI();
  Serial.print("signal strength (RSSI):");
  Serial.print(rssi);
  Serial.println(" dBm");
  
  // Print where to go in a browser:
  Serial.print("Tickle interface is available at: http://");
  Serial.println(ip);
}

///////////////////////////////////////////////////////////////////
//                       USER INTERFACE                          //
///////////////////////////////////////////////////////////////////

void createInterface(WiFiClient client) {

  client.println("HTTP/1.1 200 OK");
  client.println("Content-type:text/html");
  client.println();

  // Begin HTML page
  client.println("<!DOCTYPE HTML>");
  client.println("<html>");
  client.println("<head><title>Arduino WiFi + LED</title>");

  // Viewport metadata (needed to display properly on device)
  client.println("<meta name=\"viewport\" content=\"width=device-width, initial-scale=1\"></head>");

  // Controllers
  client.println("Click <a href=\"/HIGH\">here</a> turn the LED on<br>");
  client.println("Click <a href=\"/LOW\">here</a> turn the LED off<br>");
                 
  // End HTML page
  client.println("</body></html>");
}
```

