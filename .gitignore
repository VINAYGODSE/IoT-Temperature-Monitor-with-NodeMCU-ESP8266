// Include libraries
#include <ESP8266WiFi.h>
#include <DHT.h>

// Pin and sensor setup
#define DHTPIN 2        // D4 pin
#define DHTTYPE DHT11   // DHT11 sensor
DHT dht(DHTPIN, DHTTYPE);

// Wi-Fi credentials (optional for web server)
const char* ssid = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";

// Web server on port 80 (optional)
WiFiServer server(80);

void setup() {
  Serial.begin(115200);  // Start serial communication
  dht.begin();           // Initialize DHT sensor

  // Optional: Connect to Wi-Fi
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("\nConnected to Wi-Fi");
  Serial.println(WiFi.localIP());
  server.begin();  // Start the server
}

void loop() {
  // Read temperature and humidity
  float temp = dht.readTemperature();  // Celsius
  float humid = dht.readHumidity();

  // Check if readings are valid
  if (isnan(temp) || isnan(humid)) {
    Serial.println("Failed to read from DHT sensor!");
    delay(2000);
    return;
  }

  // Print to Serial Monitor
  Serial.print("Temperature: ");
  Serial.print(temp);
  Serial.print(" °C, Humidity: ");
  Serial.print(humid);
  Serial.println(" %");

  // Optional: Serve data via web server
  WiFiClient client = server.available();
  if (client) {
    client.println("HTTP/1.1 200 OK");
    client.println("Content-Type: text/html");
    client.println();
    client.print("<h1>Temperature: ");
    client.print(temp);
    client.print(" °C</h1><h1>Humidity: ");
    client.print(humid);
    client.println(" %</h1>");
    client.stop();
  }

  delay(2000);  // Update every 2 seconds
}
