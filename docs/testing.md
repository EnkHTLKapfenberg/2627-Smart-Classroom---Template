# Systemtests

Tests sollen Anforderungen und wichtige Fehlerfälle nachvollziehbar prüfen.

## Testübersicht

| ID | Anforderung | Test/Durchführung | Erwartetes Ergebnis | Tatsächliches Ergebnis | Status |
|---|---|---|---|---|---|
| T01 | M01 | | | | ⬜ |
| T02 | M02 | | | | ⬜ |

Status beispielsweise: ⬜ offen / ✅ bestanden / ❌ fehlgeschlagen.

## Integrationstests

Berücksichtigt abhängig vom System insbesondere:

- Normalbetrieb
- ungültige Sensordaten
- Sensorausfall
- WLAN-Unterbrechung
- MQTT-Verbindungsabbruch
- Neustart des Mikrocontrollers
- Neustart zentraler Dienste
- gleichzeitiger Betrieb aller Smart-Classroom-Geräte

## Ausführliche Testbeschreibungen

Für komplexere Tests:

### Txx – Titel

**Voraussetzung:**  
...

**Durchführung:**  
...

**Erwartetes Ergebnis:**  
...

**Tatsächliches Ergebnis:**  
...

**Ergebnis / Folgemaßnahmen:**  
...
