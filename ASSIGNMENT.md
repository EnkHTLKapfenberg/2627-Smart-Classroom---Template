# SEN-Projektarbeit 2026/27 – Smart Classroom

## 1. Ziel

Ihr entwickelt in Teams ein Teilsystem für einen intelligenten Klassenraum. Sensoren und gegebenenfalls Aktoren werden mit einem Mikrocontroller verbunden. Prozessdaten werden lokal verarbeitet, über MQTT übertragen, in Home Assistant integriert, gespeichert und mit Grafana ausgewertet.

Das gemeinsame Ziel ist ein verteiltes Automatisierungssystem:

**Sensoren/Aktoren → Mikrocontroller → lokale Datenverarbeitung → MQTT → Home Assistant → Datenspeicherung → Grafana**

## 2. Organisation

Die Arbeit erfolgt grundsätzlich in Zweiergruppen. Eine Dreiergruppe übernimmt zusätzlich die Einrichtung und Betreuung der gemeinsamen Serverinfrastruktur auf einem Raspberry Pi.

Jede Gruppe entwickelt ein eigenes Teilsystem und ein eigenes Grafana-Dashboard.

## 3. GitHub ist verbindlich

GitHub ist die zentrale Plattform für Softwareentwicklung und Projektorganisation. Der Entwicklungsprozess muss nachvollziehbar sein.

Verwendet werden insbesondere:

- Issues für konkrete Aufgaben und Fehler,
- ein GitHub Project für den Arbeitsstatus,
- Milestones für Projektphasen,
- Feature-/Fix-Branches für größere Änderungen,
- Commits mit aussagekräftigen Nachrichten,
- Pull Requests für größere abgeschlossene Änderungen,
- Reviews durch ein anderes Gruppenmitglied,
- die Dokumentation in diesem Repository.

Nicht nachvollziehbar dokumentierte lokale Arbeit kann bei der Beurteilung nicht ausreichend berücksichtigt werden.

### Empfohlener Workflow

Issue → Branch → Implementierung → Commits → Pull Request → Review/Test → Merge → Done

Pro Schüler/in soll normalerweise nur **ein Issue gleichzeitig** den Status `In Progress` besitzen.

## 4. Projektphase M1 – Konzept

Dokumentiert eure vorhandenen Sensor- und Aktorideen in `PROJECT.md`.

Für Sensoren sind mindestens Messgröße, Zweck, entstehende Daten, ungefähre Änderungsgeschwindigkeit und mögliche Auswertungen zu beschreiben.

Für Aktoren sind Aufgabe, Auslöser und benötigte Sensorinformationen zu beschreiben.

Die Vorschläge werden anschließend technisch und inhaltlich abgestimmt.

Erstellt danach überprüfbare Muss-, Soll- und Kann-Anforderungen in `docs/requirements.md`.

## 5. Projektphase M2 – Architektur

Plant Hardware, Software und Datenfluss. Dokumentiert die Architektur in `docs/architecture.md`.

Die Planung umfasst mindestens:

- Hardwarekomponenten und Schnittstellen,
- Aufgaben des Mikrocontrollers,
- Aufgaben der zentralen Systeme,
- Softwarekomponenten,
- objektorientiertes Klassenmodell,
- verwendete Datenstrukturen,
- Datenfluss vom Sensor bis zur Visualisierung.

## 6. Projektphase M3 – Smart Sensor

Implementiert die Sensor-/Aktorsoftware modular und objektorientiert.

Ein Smart Sensor soll nicht nur Rohwerte übertragen. Die Verarbeitungskette lautet grundsätzlich:

**Messwert erfassen → prüfen → verarbeiten → bewerten → übertragen**

Je nach Messgröße sind beispielsweise sinnvoll:

- Plausibilitätsprüfung,
- Mittelwert oder gleitender Mittelwert,
- Minimum/Maximum,
- Median,
- Ringbuffer,
- Filter,
- Ausreißererkennung,
- Schwellwerte,
- Trend- oder Ereigniserkennung.

Mindestens ein geeignetes Verfahren zur Verarbeitung der Prozessdaten muss umgesetzt und begründet werden.

Verwendet geeignete Datenstrukturen wie Arrays, Klassen, Queues oder Ringbuffer und begründet wesentliche Entscheidungen.

## 7. Objektorientierte Entwicklung

Die Software muss modular und objektorientiert aufgebaut sein. Mögliche Komponenten sind beispielsweise `Sensor`, `Measurement`, `DataBuffer`, `Filter`, `MqttClient`, `Configuration` und `Actuator`.

Das tatsächliche Klassenmodell richtet sich nach eurem Projekt und wird in `docs/architecture.md` dokumentiert.

## 8. Projektphase M4 – MQTT und Home Assistant

Alle Gruppen verwenden eine gemeinsam abgestimmte MQTT-Struktur. Eine mögliche Grundstruktur ist:

`smartclassroom/<raum>/<device>/<measurement>`

Die vollständige Schnittstelle wird in `docs/mqtt.md` dokumentiert.

Das Gerät muss Daten veröffentlichen und mindestens eine sinnvolle Funktion über MQTT empfangen können, beispielsweise Messintervall, Grenzwert, Betriebsmodus, Aktorbefehl oder Reset.

Berücksichtigt Verbindungsabbrüche und automatische Wiederverbindung.

In Home Assistant werden sinnvolle Entitäten mit Namen, Einheiten, Verfügbarkeit und Gerätezuordnung eingerichtet.

## 9. Projektphase M5 – Daten und Dashboard

Jede Gruppe erstellt ein eigenes Grafana-Dashboard.

Es soll aktuelle und historische Daten kombinieren und mindestens eine tatsächliche Auswertung enthalten, beispielsweise Mittelwerte, Min/Max, Trends, Grenzwertüberschreitungen oder Ereignisse.

Die zentrale Frage lautet:

> Welche Informationen benötigt ein Benutzer, um anhand unserer Messdaten den Zustand des Klassenzimmers beurteilen zu können?

Dokumentation und Exporte werden unter `grafana/` abgelegt.

## 10. Projektphase M6 – Integration und Abschluss

Alle Teilsysteme werden gemeinsam betrieben und getestet.

Mindestens zu berücksichtigen sind:

- Normalbetrieb,
- ungültige Sensordaten,
- Sensorausfall,
- WLAN-Unterbrechung,
- MQTT-Verbindungsabbruch,
- Neustart des Mikrocontrollers,
- Neustart zentraler Dienste,
- gleichzeitiger Betrieb aller Geräte.

Tests werden in `docs/testing.md` nachvollziehbar dokumentiert.

Analysiert außerdem mindestens einen Teil eurer Software hinsichtlich Datenstruktur, Speicherbedarf, Algorithmuseffizienz, unnötigem MQTT-Verkehr, blockierendem Code oder Erweiterbarkeit. Beschreibt eine konkrete Optimierung und setzt sie, sofern sinnvoll, um.

## 11. Zusatzaufgabe der Dreiergruppe – Server

Die Dreiergruppe richtet die gemeinsame Serverinfrastruktur auf einem Raspberry Pi ein. Dazu gehören die für das Projekt benötigten Dienste, insbesondere Home Assistant, MQTT-Broker, Datenspeicherung und Grafana.

Zu dokumentieren sind Hardware, Betriebssystem, Dienste, Netzwerk, Hostnamen, Ports, MQTT-Konfiguration, Benutzer-/Berechtigungskonzept, Backup und Wiederanlauf nach einem Neustart.

Zugangsdaten dürfen nicht im Repository gespeichert werden.

## 12. Anforderungen an Git

Jede Person arbeitet mit dem eigenen GitHub-Account.

Commit-Nachrichten müssen Änderungen beschreiben, zum Beispiel:

- `feat: add temperature sensor class`
- `feat: calculate moving average`
- `fix: reconnect MQTT after WiFi loss`
- `docs: document MQTT topics`
- `test: add plausibility test`

Nicht geeignet sind Nachrichten wie `update`, `fertig`, `test` oder `version2`.

Die Anzahl der Commits ist kein Bewertungskriterium. Entscheidend sind Qualität, technische Schwierigkeit, Selbstständigkeit und Nachvollziehbarkeit.

## 13. Abschluss

Am Ende präsentiert jede Gruppe ein funktionsfähiges Teilsystem:

**Sensorik/Aktorik + Mikrocontroller + lokale Datenverarbeitung + MQTT + Home Assistant + Datenspeicherung + eigenes Grafana-Dashboard**

Zusätzlich muss das Repository den Entwicklungsprozess nachvollziehbar dokumentieren. Jedes Gruppenmitglied muss die grundlegende Architektur und Funktionsweise des gesamten eigenen Systems erklären können.
