# ESP32 Sensor Node

A small project using an ESP32 dev board to measure temperature and humidity, then publish data over MQTT.  
I built it to feed real-time environmental data into my homelab dashboard.

---

## Hardware

- ESP32 DevKit board
- DHT22 temperature/humidity sensor
- Breadboard + jumper wires
- 5V USB power

---

## Firmware

Arduino-based sketch with `PubSubClient` library. On boot, connects to Wi-Fi, reads sensor values every 30s, and publishes to an MQTT topic.

```cpp
#include <WiFi.h>
#include <PubSubClient.h>
#include "DHT.h"

// config trimmed for clarity

DHT dht(4, DHT22);

void loop() {
  float t = dht.readTemperature();
  float h = dht.readHumidity();
  char buf[64];
  snprintf(buf, sizeof(buf), "{\"temp\": %.1f, \"hum\": %.1f}", t, h);
  client.publish("homelab/sensor1", buf);
  delay(30000);
}
