# Verbindlicher MQTT-Standard

Dieser Standard gilt für den ESPHome-Prototyp und unverändert für die spätere Arduino-/FreeRTOS-Lösung. Abweichungen benötigen ein dokumentiertes Issue und die Zustimmung der Lehrperson.

## 1. Bezeichner

Alle Bezeichner verwenden nur Kleinbuchstaben, Ziffern und Bindestriche.

- `group_id`: eindeutige Gruppe, z. B. `group-07`
- `device_id`: eindeutiges ESP32-Gerät innerhalb der Gruppe, z. B. `acoustic-node`
- `object_id`: eindeutige Messgröße, Zustandsgröße oder Funktion, z. B. `sound-level`
- `node_id`: für MQTT Discovery stabil aus `group_id` und `device_id`, z. B. `group-07-acoustic-node`

Diese IDs bleiben über beide Entwicklungsstufen stabil.

## 2. Topic-Struktur

Topic-Basis:

`smartclassroom/<group_id>/<device_id>`

| Zweck | verbindliches Topic | Retain |
|---|---|---|
| Messwert / Zustand | `smartclassroom/<group_id>/<device_id>/state/<object_id>` | ja |
| Verfügbarkeit | `smartclassroom/<group_id>/<device_id>/availability` | ja |
| Betriebszustand | `smartclassroom/<group_id>/<device_id>/status` | ja |
| Befehl | `smartclassroom/<group_id>/<device_id>/command/<object_id>` | nein |
| TTS-Anforderung | `smartclassroom/shared/tts/request` | nein |

Sensor- und Zustands-Topics werden veröffentlicht. Command-Topics werden nur abonniert, wenn das Gerät eine klar dokumentierte Funktion sicher ausführen kann.

## 3. Payloads

Messwerte und abgeleitete Zustände verwenden JSON:

```json
{
  "value": 742,
  "unit": "ppm",
  "quality": "valid",
  "timestamp": "2026-10-15T09:30:00Z"
}
```

Pflichtfelder:

- `value`: Zahl, Boolean oder definierter Zustandsstring
- `unit`: SI-Einheit beziehungsweise dokumentierte Einheit; bei einheitslosen Werten `""`
- `quality`: `valid`, `invalid`, `uncertain` oder `stale`
- `timestamp`: ISO-8601-Zeitstempel in UTC, sofern eine gültige Zeit verfügbar ist

Ungültige Messungen dürfen nicht als normale gültige Werte erscheinen. Der Qualitätsstatus muss den Fehler sichtbar machen.

Betriebszustand auf `.../status`:

```json
{
  "state": "running",
  "uptime_s": 3600,
  "firmware": "1.0.0",
  "rssi_dbm": -58,
  "error": null
}
```

Für `state` sind mindestens `starting`, `running`, `degraded` und `error` vorgesehen.

Befehle verwenden ebenfalls JSON, beispielsweise:

```json
{
  "value": 30,
  "request_id": "group-02-0042"
}
```

Keine Payload enthält Passwörter, Tokens, WLAN-Zugangsdaten oder andere Geheimnisse.

## 4. Availability, Last Will und Wiederverbindung

Beim Verbinden setzt jeder MQTT-Client ein retained Last Will and Testament (LWT):

- Topic: `smartclassroom/<group_id>/<device_id>/availability`
- Payload: `offline`
- QoS: mindestens 1
- Retain: `true`

Nach erfolgreicher Verbindung veröffentlicht das Gerät auf demselben Topic retained `online`. Bei einem Verbindungsabbruch startet es automatisch eine Wiederverbindung mit begrenzter Wartezeit und ohne blockierende Endlosschleife. Messwerterfassung und sichere lokale Funktionen laufen soweit möglich weiter. Nach erfolgreicher Wiederverbindung werden Availability, Betriebszustand, aktuelle Zustände und MQTT-Discovery-Konfiguration erneut veröffentlicht.

## 5. Home Assistant MQTT Discovery

Alle Sensoren und relevanten Zustände müssen automatisch in Home Assistant erscheinen. Das Discovery-Topic lautet:

`homeassistant/<component>/<node_id>/<object_id>/config`

Geeignete `component`-Werte sind beispielsweise `sensor`, `binary_sensor`, `switch`, `number` oder `button`.

Jede Discovery-Payload enthält mindestens:

- `name`
- stabile `unique_id`, z. B. `group-07-acoustic-node-sound-level`
- `state_topic`
- `availability_topic`
- `value_template`, wenn der State als JSON übertragen wird
- korrekte `unit_of_measurement`, wenn der Wert eine Einheit besitzt
- passende `device_class` und gegebenenfalls `state_class`
- `device`-Metadaten mit `identifiers`, `name`, `manufacturer`, `model` und `sw_version`

Beispiel ohne Geheimnisse:

```json
{
  "name": "Sound level",
  "unique_id": "group-07-acoustic-node-sound-level",
  "state_topic": "smartclassroom/group-07/acoustic-node/state/sound-level",
  "availability_topic": "smartclassroom/group-07/acoustic-node/availability",
  "payload_available": "online",
  "payload_not_available": "offline",
  "value_template": "{{ value_json.value }}",
  "unit_of_measurement": "dB",
  "device_class": "sound_pressure",
  "state_class": "measurement",
  "device": {
    "identifiers": ["group-07-acoustic-node"],
    "name": "Group 07 Acoustic Node",
    "manufacturer": "HTL Kapfenberg",
    "model": "ESP32 Smart Sensor",
    "sw_version": "1.0.0"
  }
}
```

Discovery wird beim Start und nach jeder MQTT-Wiederverbindung retained veröffentlicht. ESPHome und Arduino/FreeRTOS müssen dieselben Topics, IDs, Einheiten und Geräte-Metadaten verwenden.

## 6. TTS-Aktor auf dem Raspberry Pi

Der Lautsprecher befindet sich am selben Raspberry Pi wie Home Assistant. Die zentrale TTS-Ausgabe wird ausschließlich von Home Assistant ausgelöst und liegt in der Verantwortung von Gruppe 7. Keine Gruppe erhält direkten Shell-Zugriff auf den Raspberry Pi.

Andere Gruppen dürfen TTS nur über folgende gruppenübergreifende Schnittstelle anfordern:

- MQTT-Topic: `smartclassroom/shared/tts/request`
- Verarbeitung: freigegebene Home-Assistant-Automatisierung
- keine direkte Lautsprecher-, Shell- oder Betriebssystemsteuerung

Payload:

```json
{
  "source": "group-03",
  "message": "Bitte den Raum lüften.",
  "priority": "normal",
  "volume": 0.35
}
```

Regeln:

- `source`: gültige `group_id`
- `message`: kurzer, sachlicher Text ohne personenbezogene, beleidigende oder störende Inhalte
- `priority`: `low`, `normal` oder `high`; Home Assistant entscheidet über Reihenfolge und Ausgabe
- `volume`: Zahl von 0.0 bis maximal 0.5; höhere Werte werden verworfen oder auf 0.5 begrenzt
- Home Assistant validiert Quelle, Länge, Priorität, Rate und Lautstärke.
- Die Schnittstelle enthält keine Geheimnisse und erlaubt keine beliebigen Dienste oder Shell-Befehle.

## 7. Projektspezifische Schnittstellen

Ergänzt eure tatsächlichen Schnittstellen:

| object_id | State-/Command-Topic | Datentyp | Einheit | quality / Wertebereich | Intervall / Ereignis |
|---|---|---|---|---|---|
| … | … | … | … | … | … |

Begründet Intervalle und ereignisgesteuerte Übertragungen. Vermeidet unnötigen MQTT-Verkehr.
