# Projektbeschreibung – ausfüllbare Vorlage

> Diese Datei beschreibt dauerhaft Projektidee, Anforderungen auf Überblicksebene und Architektur. Sie enthält **keinen laufenden Projektstatus**. Aufgaben, Verantwortlichkeiten und Fortschritt werden ausschließlich über GitHub Issues und das GitHub Project verwaltet.

## 1. Gruppenname

**Gruppenname:** …

## 2. Teammitglieder und GitHub-Namen

| Name | GitHub-Benutzername |
|---|---|
| … | @… |
| … | @… |

## 3. Gruppenthema

**Gewähltes Thema aus [GROUPS.md](GROUPS.md):** …

Beschreibt kurz, wie ihr das Thema fachlich interpretiert.

## 4. Problemstellung

Welches konkrete Problem oder welche Fragestellung im Klassenraum soll euer System untersuchen oder lösen?

…

## 5. Sensoren

Die konkrete Auswahl erfolgt in M1/M2 und muss begründet werden.

| Messgröße | geplanter Sensor / Prinzip | Zweck | Auswahlbegründung |
|---|---|---|---|
| … | … | … | … |

## 6. Aktoren

| Aktor / Ausgabe | Aufgabe | Auslöser | Sicherheitsgrenzen |
|---|---|---|---|
| … | … | … | … |

Falls keine Aktoren verwendet werden, begründet dies.

## 7. Gewählter Softwarestack

- **ESPHome-Prototyp:** …
- **Verpflichtende Arduino-/FreeRTOS-Lösung:** …
- **Bibliotheken und Versionen:** …
- **Home Assistant / Grafana:** …

Beschreibt den geplanten Übergang von ESPHome zur eigenen Arduino-/FreeRTOS-Implementierung.

## 8. Lokale Datenverarbeitung

Welche Verarbeitung erfolgt direkt auf dem ESP32? Welcher abgeleitete Zustandswert entsteht?

| Eingangsdaten | Verfahren | abgeleiteter Zustand | Begründung |
|---|---|---|---|
| … | z. B. gleitender Mittelwert | … | … |

## 9. Datenfluss

Beispiel: Sensor → ESP32 → Prüfung → lokale Verarbeitung → Zustandsbildung → MQTT → Home Assistant → Datenspeicherung → Grafana

**Unser Datenfluss:** …

## 10. MQTT-Schnittstellen

Verweist auf den [MQTT-Standard](docs/mqtt.md) und nennt eure vorgesehenen `group_id`, `device_id`, Messwerte, Zustände und Befehle.

…

## 11. Abgrenzung

Welche Aufgaben übernimmt euer Teilsystem? Was gehört ausdrücklich nicht zum Projektumfang? Welche Aufgaben übernehmen andere Gruppen oder zentrale Dienste?

…

## 12. Sicherheits- und Datenschutzbetrachtung

Beschreibt Gefahren, personenbezogene oder pseudonymisierte Daten, technische Schutzmaßnahmen und verbleibende Risiken. Beachtet insbesondere 230 V, Schulhardware, Audio, Bluetooth/ESPresense, TTS und Zugangsdaten.

…

## 13. Abnahmekriterien

Formuliert überprüfbare Kriterien und verweist auf IDs aus [docs/requirements.md](docs/requirements.md).

- [ ] …
- [ ] …
