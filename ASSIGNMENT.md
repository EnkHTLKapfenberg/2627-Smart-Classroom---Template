# SEN-Projektarbeit 2026/27 – Smart Classroom

## 1. Ziel

Ihr entwickelt in Teams ein Teilsystem für einen intelligenten Klassenraum. Sensoren und gegebenenfalls Aktoren werden mit einem Mikrocontroller verbunden. Prozessdaten werden lokal verarbeitet, über MQTT übertragen, in Home Assistant integriert, gespeichert und mit Grafana ausgewertet.

Das gemeinsame Ziel ist ein verteiltes Automatisierungssystem:

**Sensoren/Aktoren → Mikrocontroller → lokale Datenverarbeitung → MQTT → Home Assistant → Datenspeicherung → Grafana**

## 2. Organisation

Die Arbeit erfolgt grundsätzlich in Zweiergruppen. Eine Dreiergruppe übernimmt zusätzlich die Einrichtung und Betreuung der gemeinsamen Serverinfrastruktur auf einem Raspberry Pi.

Jede Gruppe entwickelt ein eigenes Teilsystem und ein eigenes Grafana-Dashboard. Jede Gruppe entwickelt dabei einen **eigenen ESP32-basierten Smart Sensor**. Die reine Integration bereits vorhandener Geräte oder Dienste erfüllt die Aufgabenstellung nicht.

## 3. Verbindliche GitHub-Arbeitsweise

GitHub ist die zentrale Plattform für Softwareentwicklung und Projektorganisation. Der Entwicklungsprozess muss für alle Gruppenmitglieder und die Lehrperson jederzeit nachvollziehbar sein. Nicht nachvollziehbar dokumentierte lokale Arbeit kann bei der Beurteilung nicht ausreichend berücksichtigt werden.

Die verbindliche Kette für jede relevante Änderung lautet:

**Anforderung → Issue → Assignee/Milestone/Labels → Branch → Commits → Pull Request → Review/Test → Done**

### 3.1 Maßgebliche Informationsquellen

- `PROJECT.md` beschreibt dauerhaft die Projektidee, die Anforderungen auf Überblicksebene und die Architektur. Die Datei enthält ausdrücklich **keinen laufenden Projektstatus**, keine aktuelle Aufgabenliste und keine Fortschrittsangaben.
- **GitHub Issues und das GitHub Project sind die einzige maßgebliche Quelle** für aktuelle Aufgaben, Verantwortlichkeiten und den Projektfortschritt.
- Änderungen an Anforderungen oder Architektur werden in der zugehörigen Dokumentation festgehalten und als Issue geplant und umgesetzt.

### 3.2 Issues als zentrale Arbeitspakete

Jedes relevante Arbeitspaket wird **vor Beginn der Arbeit** als GitHub Issue erfasst. Mündliche Absprachen, private Notizen oder eine Aufgabenliste in `PROJECT.md` ersetzen kein Issue.

Es gibt zwei grundlegende Arten:

- **Task-Issue:** Eine geplante neue Funktion, Verbesserung, Dokumentation, Untersuchung oder ein Test. Das erwartete Ergebnis wird vor der Umsetzung beschrieben.
- **Bug-Issue:** Ein vorhandenes Verhalten weicht vom erwarteten Verhalten ab. Das Issue beschreibt mindestens das beobachtete Verhalten, das erwartete Verhalten und – soweit bekannt – Schritte zum Reproduzieren.

Jedes Issue enthält verpflichtend:

- ein eindeutiges, überprüfbares Ziel,
- konkrete Arbeitsschritte als Checkliste,
- Akzeptanzkriterien beziehungsweise eine projektspezifische **Definition of Done**,
- mindestens einen Assignee,
- passende Labels,
- **genau einen** passenden Milestone von M1 bis M6,
- einen aktuellen Status im GitHub Project.

Große Issues werden in kleinere, einzeln überprüfbare Issues geteilt. Ein Issue soll so abgegrenzt sein, dass sein Ergebnis in einem Pull Request sinnvoll geprüft werden kann.

### 3.3 Milestones M1 bis M6

Jedes Issue wird jener Projektphase zugeordnet, in der sein Ergebnis benötigt und überprüft wird:

| Milestone | Inhalt und Zuordnung |
|---|---|
| **M1 – Konzept** | Projektidee, Sensor-/Aktorideen, Nutzen, Muss-/Soll-/Kann-Anforderungen und fachliche Abstimmung |
| **M2 – Architektur** | Hardware- und Softwarearchitektur, Schnittstellen, Klassenmodell, Datenstrukturen und Datenfluss |
| **M3 – Smart Sensor** | Sensor-/Aktorsoftware, lokale Verarbeitung, Plausibilisierung, Filter, Auswertungen und modulare Implementierung |
| **M4 – Kommunikation** | MQTT-Struktur, Senden und Empfangen, Wiederverbindung sowie Integration in Home Assistant |
| **M5 – Daten & Dashboard** | Datenspeicherung, Grafana-Dashboard, historische Daten und aussagekräftige Auswertungen |
| **M6 – Integration & Abschluss** | Gesamtsystem, Fehler- und Integrationstests, Optimierung, Abschlussdokumentation und Präsentation |

Ein Issue erhält nicht den Milestone der gerade aktuellen Kalenderphase, sondern den Milestone, zu dessen Ergebnis es fachlich gehört.

### 3.4 Verbindliche Labels

Mindestens ein Label für die **Art** und mindestens ein Label für den **betroffenen Bereich** werden vergeben. Wenn mehrere Bereiche betroffen sind, werden mehrere Bereichslabels verwendet.

**Art:**

- `feature`: neue Funktion oder funktionale Verbesserung
- `bug`: Fehlerbehebung
- `documentation`: Erstellung oder Änderung von Dokumentation
- `test`: Erstellung, Erweiterung oder Durchführung von Tests

**Bereich:**

- `firmware`: Mikrocontroller-Software und gerätenahe Logik
- `sensor`: Sensoranbindung und Messwertverarbeitung
- `actuator`: Aktoransteuerung
- `mqtt`: MQTT-Themen, Nachrichten und Verbindungslogik
- `home-assistant`: Home-Assistant-Integration
- `grafana`: Dashboard und Visualisierung
- `server`: zentrale Dienste, Netzwerk und Serverinfrastruktur

**Zusätzliche Labels:**

- `blocked`: Die Arbeit kann wegen einer konkreten Abhängigkeit oder eines Problems nicht sinnvoll fortgesetzt werden.
- `help-wanted`: Es wird gezielt Unterstützung durch ein Gruppenmitglied oder die Lehrperson benötigt.

Beispiel: Eine neue Temperaturmessung mit MQTT-Übertragung kann gleichzeitig `feature`, `sensor`, `firmware` und `mqtt` erhalten.

### 3.5 GitHub Project und Statusübergänge

Jedes offene Issue befindet sich im GitHub Project und hat genau einen aktuellen Status:

| Status | Eintrittskriterium | Nächster regulärer Übergang |
|---|---|---|
| **Backlog** | Das Arbeitspaket ist erfasst, aber noch nicht ausreichend geklärt oder noch nicht zur Umsetzung vorgesehen. | Nach Klärung von Ziel, Checkliste, DoD, Assignee, Labels und Milestone zu **Ready**. |
| **Ready** | Das Issue ist vollständig beschrieben, nicht blockiert und kann ohne weitere Grundsatzentscheidung begonnen werden. | Bei tatsächlichem Arbeitsbeginn und angelegtem Branch zu **In Progress**. |
| **In Progress** | Mindestens ein Assignee arbeitet aktiv am Issue; der zugehörige Branch und erste nachvollziehbare Arbeitsschritte existieren. | Sobald Umsetzung und eigene Tests abgeschlossen sind und ein PR bereit zur Prüfung ist, zu **Review**. |
| **Review** | Ein Pull Request ist geöffnet, mit dem Issue verknüpft und für Review sowie Test bereit. | Bei Änderungsbedarf zurück zu **In Progress**; nach erfolgreichem Test, Review und Merge zu **Done**. |
| **Done** | Die vollständige Definition of Done ist erfüllt, der PR ist gemergt und das Issue ist geschlossen. | Kein weiterer Übergang. Neue Nacharbeit wird als neues Issue erfasst. |

Normalerweise darf pro Schüler/in nur **ein Issue gleichzeitig** den Status `In Progress` besitzen. Eine Ausnahme muss im betroffenen Issue begründet und innerhalb der Gruppe abgestimmt werden.

### 3.6 Branches, Commits und Pull Requests

Entwicklungsarbeit erfolgt nicht direkt auf `main`. Für jedes Issue wird ein eigener Branch erstellt. Der Branchname enthält Art, Issue-Nummer und einen kurzen Inhalt, zum Beispiel:

- `feature/issue-17-moving-average`
- `fix/issue-24-mqtt-reconnect`
- `docs/issue-31-architecture`

Commits werden regelmäßig, klein und inhaltlich zusammengehörig erstellt. Die Nachricht beschreibt die Änderung und stellt, wenn sinnvoll, den Bezug zum Issue her, zum Beispiel:

- `feat: add moving average (#17)`
- `fix: reconnect MQTT after WiFi loss (#24)`
- `docs: document MQTT topics (#31)`
- `test: add plausibility checks (#42)`

Nicht geeignet sind Nachrichten wie `update`, `fertig`, `test` oder `version2`. Die Anzahl der Commits ist kein Bewertungskriterium. Entscheidend sind Qualität, technische Schwierigkeit, Selbstständigkeit und Nachvollziehbarkeit.

Nach Abschluss der Umsetzung wird ein Pull Request gegen `main` geöffnet. Er muss:

- das Issue mit `Closes #17` verknüpfen,
- die durchgeführten Änderungen verständlich beschreiben,
- die ausgeführten Tests und deren Ergebnis nennen,
- die Checkliste und Definition of Done des Issues erfüllen.

Mindestens ein Gruppenpartner führt das Review durch. Gefundene Mängel werden vor dem Merge korrigiert und erneut geprüft. Erst nach erfolgreichem Test, positivem Review und Merge darf das Issue geschlossen und im Project nach `Done` verschoben werden.

### 3.7 Allgemeine Definition of Done

Ein Issue ist erst fertig, wenn mindestens alle folgenden Punkte erfüllt sind:

- [ ] Akzeptanzkriterien des Issues sind erfüllt.
- [ ] Funktion beziehungsweise Änderung wurde getestet; Ergebnis und Testvorgehen sind nachvollziehbar.
- [ ] Der vollständige Code beziehungsweise alle geänderten Dateien befinden sich auf GitHub.
- [ ] Es wurden keine Passwörter, Tokens, privaten Schlüssel oder anderen Zugangsdaten eingecheckt.
- [ ] Betroffene Dokumentation wurde aktualisiert.
- [ ] Ein Pull Request wurde von mindestens einem Gruppenpartner geprüft und anschließend gemergt.
- [ ] Das Issue ist geschlossen und der Project-Status lautet `Done`.

Zusätzliche projektspezifische Kriterien werden direkt im jeweiligen Issue ergänzt.

### 3.8 Umgang mit Problemen und Blockaden

Wenn eine echte Blockade die Weiterarbeit verhindert, wird sofort das Label `blocked` gesetzt. Im Issue werden dokumentiert:

- die konkrete Ursache,
- bereits durchgeführte Lösungsversuche,
- welche Entscheidung, Information oder Hilfe benötigt wird,
- wer die Blockade nach Möglichkeit lösen kann.

Wenn Unterstützung benötigt wird, wird zusätzlich `help-wanted` gesetzt. Blockaden dürfen nicht still liegen bleiben: Sie werden im Issue aktualisiert und zeitnah in der Gruppe beziehungsweise mit der Lehrperson besprochen. Nach Beseitigung der Ursache wird `blocked` entfernt und der Status passend aktualisiert.

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

Jede Gruppe entwickelt einen eigenen ESP32-basierten Smart Sensor. Für jeden Smart Sensor gelten folgende Mindestanforderungen:

1. Er besitzt eigene ESP32-Hardware.
2. Er wird zuerst mit ESPHome und danach mit Arduino unter Verwendung von FreeRTOS umgesetzt.
3. Er erfasst Messwerte lokal.
4. Er erkennt ungültige Werte.
5. Er führt mindestens eine lokale Verarbeitung durch.
6. Er berechnet mindestens einen abgeleiteten Zustandswert.
7. Er veröffentlicht Daten über MQTT.
8. Er meldet seinen Betriebszustand.
9. Er verbindet sich nach WLAN- oder MQTT-Verbindungsabbrüchen selbstständig wieder.
10. Er wird über MQTT Discovery in Home Assistant eingebunden.
11. Er stellt Daten für Grafana bereit.
12. Er wird getestet und dokumentiert.

Die verbindliche Entwicklungsabfolge lautet:

1. Zuerst wird ein funktionsfähiger **ESPHome-Prototyp** erstellt.
2. Danach wird verpflichtend eine **eigene Arduino-/FreeRTOS-Lösung** entwickelt. Darin müssen Erfassung, Verarbeitung, Zustandsbildung, MQTT-Kommunikation und Fehlerbehandlung im eigenen Programm nachvollziehbar implementiert sein.

Ein Smart Sensor überträgt nicht nur Rohwerte. Die Verarbeitungskette lautet grundsätzlich:

**Messwert erfassen → prüfen → verarbeiten → Zustand ableiten → übertragen**

Als lokale Verarbeitung eignen sich beispielsweise:

- gleitender Mittelwert,
- Minimum/Maximum,
- Trend,
- Hysterese,
- Ausreißererkennung,
- Sensorfusion,
- Zustandsautomat,
- Plausibilitätsprüfung,
- Ereigniserkennung.

Mindestens ein geeignetes Verfahren zur Verarbeitung der Prozessdaten muss umgesetzt und begründet werden. Verwendet geeignete Datenstrukturen wie Arrays, Klassen, Queues oder Ringbuffer und begründet wesentliche Entscheidungen.

## 7. Objektorientierte Entwicklung

Die Software muss modular und objektorientiert aufgebaut sein. Mögliche Komponenten sind beispielsweise `Sensor`, `Measurement`, `DataBuffer`, `Filter`, `MqttClient`, `Configuration` und `Actuator`.

Das tatsächliche Klassenmodell richtet sich nach eurem Projekt und wird in `docs/architecture.md` dokumentiert.

## 8. Projektphase M4 – MQTT und Home Assistant

Alle Gruppen halten den verbindlichen [MQTT-Standard](docs/mqtt.md) ein. Die Topic-Basis lautet:

`smartclassroom/<group_id>/<device_id>/...`

Die Schnittstelle muss sowohl beim ESPHome-Prototyp als auch bei der späteren Arduino-/FreeRTOS-Lösung eingehalten und in `docs/mqtt.md` projektspezifisch ergänzt werden. Alle Sensoren müssen über MQTT Discovery automatisch in Home Assistant erscheinen.

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

## 12. Sicherheit und Datenschutz

Folgende Regeln gelten verbindlich:

- Es werden keine offenen Arbeiten an 230 V durchgeführt.
- Schulhardware darf nicht verändert oder beschädigt werden.
- Die Schulinfrastruktur – insbesondere Leitungen, Jalousien und feste Installationen – darf nicht verändert werden.
- Audioaufzeichnungen sind verboten. Bei Mikrofonen dürfen ausschließlich lokale Lautstärke- oder Pegelwerte erfasst und weiterverarbeitet werden. Audiodaten dürfen weder gespeichert noch übertragen werden.
- Passwörter, Tokens, WLAN-Zugangsdaten, private Schlüssel und andere Geheimnisse dürfen nicht in das Repository committed werden.
- Bei ESPresense und anderer Bluetooth-Präsenzerkennung werden Gerätekennungen pseudonymisiert. Klarnamen, persönliche Gerätebezeichnungen und dauerhaft zuordenbare Rohkennungen dürfen nicht veröffentlicht oder gespeichert werden.
- TTS wird verantwortungsvoll eingesetzt: nur sachliche, schulbezogene Nachrichten, begrenzte Lautstärke und keine beleidigenden, diskriminierenden, personenbezogenen oder störenden Ausgaben. Die zentrale Ausgabe erfolgt ausschließlich über die freigegebene Home-Assistant-Schnittstelle; Gruppen erhalten keinen Shell-Zugriff auf den Raspberry Pi.

Sicherheits- und Datenschutzrisiken sowie die vorgesehenen Schutzmaßnahmen werden in `PROJECT.md` dokumentiert und getestet, soweit sie technisch prüfbar sind.

## 13. Abschluss

Am Ende präsentiert jede Gruppe ein funktionsfähiges Teilsystem:

**Sensorik/Aktorik + Mikrocontroller + lokale Datenverarbeitung + MQTT + Home Assistant + Datenspeicherung + eigenes Grafana-Dashboard**

Zusätzlich muss das Repository den Entwicklungsprozess nachvollziehbar dokumentieren. Jedes Gruppenmitglied muss die grundlegende Architektur und Funktionsweise des gesamten eigenen Systems erklären können.
