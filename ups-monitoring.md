# UPS Monitoring

One of my goals in the homelab is **resilience**. Power outages are rare, but when they happen, I want to know exactly what’s going on.  
This project documents how I wired my UPS into a simple monitoring setup.

---

## Approach

- Connect UPS via USB to the server
- Use `nut` (Network UPS Tools) container for stats
- Script reads battery %, load, and runtime
- Data pushed into Prometheus/Grafana

---

## Example Output

battery.charge: 100
battery.runtime: 3600
input.voltage: 230.0
ups.load: 28
ups.status: OL

yaml
Kód másolása

---

## Lessons

- Even consumer-grade UPS units can be scripted into something useful  
- NUT is reliable but config-heavy — once set up, it runs for years  
- Having power data integrated into monitoring makes you sleep better