# Vevor-BLE-ESPHOME

# ESPHome – Vevor Diesel Standheizung (BLE)

Integration einer **Vevor Diesel-Standheizung mit Bluetooth (BLE)** in [ESPHome](https://esphome.io).  
Damit lässt sich die Heizung über Home Assistant oder die ESPHome-Weboberfläche komfortabel steuern und überwachen.

---

## Unterschiede zu [Bruciatore_BLE](https://github.com/edwardtfn/Bruciatore_BLE)

Diese Implementierung arbeitet mit **drei UUIDs**:

- `fff0` → Service UUID  
- `fff1` → Characteristic (Empfang, Notify)  
- `fff2` → Characteristic (Senden, Write)  

👉 Die Werte sind im Code definiert und können bei Bedarf angepasst werden.  
Dadurch ist die Lösung flexibler und auch für verschiedene Modellvarianten der Heizung nutzbar.

---

## Features

- 🔥 Heizung **Ein/Aus**  
- 🌡️ Zieltemperatur (Automatik-Modus)  
- 💨 Gebläsestufen (Manuell-Modus)  
- 🔄 Moduswechsel: Automatik ↔ Manuell  
- 🌬️ Lüftermodus  
- 🏔️ Höhenmodus (High Altitude Mode)  
- 📊 Sensoren:
  - Betriebsmodus (Manuell/Automatik) momentan nur von manuell auf Automatik
  - Heizungsstatus (inkl. Phasen: Aufwärmen, Zündung, Heizen etc.)  
  - Raumtemperatur  
  - Schalentemperatur  
  - Batteriespannung  
  - Zielwert  

---

## Voraussetzungen

- ESP32-Board (z. B. `esp32dev`)  
- Installiertes [ESPHome](https://esphome.io)  
- Vevor Diesel-Standheizung mit Bluetooth (BLE)  

---

## Installation

1. YAML in dein ESPHome-Projekt übernehmen.  
2. In den **Substitutions** anpassen:  

   ```yaml
   substitutions:
     name: bt-vevor-ble
     friendly_name: Diesel_Standheizung
     heater_mac: "XX:XX:XX:XX:XX:XX"   # MAC-Adresse eintragen
     service_uuid: "0000fff0-0000-1000-8000-00805f9b34fb"
     char_fff1_uuid: "0000fff1-0000-1000-8000-00805f9b34fb"
     char_fff2_uuid: "0000fff2-0000-1000-8000-00805f9b34fb"
