# Firmware

Hier befindet sich die Software des Smart-Sensor-/Aktor-Systems.

Die Firmware wird mit PlatformIO entwickelt. Legt das eigentliche PlatformIO-Projekt im Rahmen der Projektarbeit in diesem Verzeichnis an.

## Sicherheit

Zugangsdaten dürfen niemals committed werden. Dazu gehören insbesondere:

- WLAN-Passwörter
- MQTT-Benutzer und Passwörter
- API-Keys
- Tokens

Verwendet für lokale Zugangsdaten beispielsweise eine `secrets.h`, `.env` oder vergleichbare Datei, die durch `.gitignore` ausgeschlossen ist.

Falls die Struktur solcher Daten für andere Teammitglieder notwendig ist, erstellt eine Vorlage ohne echte Zugangsdaten, z. B. `secrets.example.h`.
