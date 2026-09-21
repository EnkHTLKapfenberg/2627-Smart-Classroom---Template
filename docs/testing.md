# Systemtests – ausfüllbare Vorlage

Jeder Test besitzt eine eindeutige ID im Format `TEST-01`, `TEST-02`, … und verweist auf mindestens eine Anforderungs-ID aus [requirements.md](requirements.md).

## Testübersicht

| Test-ID | Anforderungs-ID(s) | Test / Durchführung | erwartetes Ergebnis | tatsächliches Ergebnis | Status |
|---|---|---|---|---|---|
| TEST-01 | REQ-F-01 | Beispiel: Veröffentlichungszeitpunkte für eine Minute aufzeichnen. | Abstand höchstens 10 s | … | ⬜ offen |
| TEST-02 | REQ-NF-01 | Beispiel: MQTT-Verbindung trennen und wieder freigeben. | automatische Wiederverbindung | … | ⬜ offen |
| TEST-03 | … | … | … | … | ⬜ offen |

Status: ⬜ offen / ✅ bestanden / ❌ fehlgeschlagen.

## Verbindliche Fehler- und Integrationstests

Berücksichtigt abhängig vom System insbesondere:

- Normalbetrieb
- ungültige Sensordaten
- Sensorausfall
- WLAN-Unterbrechung
- MQTT-Verbindungsabbruch
- Neustart des ESP32
- Neustart zentraler Dienste
- gleichzeitiger Betrieb aller Smart-Classroom-Geräte
- sichere Zustände von Aktoren
- Datenschutz- und TTS-Grenzen, soweit technisch prüfbar

## Ausführliche Testbeschreibung

### TEST-XX – Titel

**Geprüfte Anforderungen:** REQ-F-XX, REQ-NF-XX

**Voraussetzungen:** …

**Testdaten / Hardware:** …

**Durchführung:**

1. …
2. …

**Erwartetes Ergebnis:** …

**Tatsächliches Ergebnis / Messwerte:** …

**Status und Folgemaßnahmen:** …
