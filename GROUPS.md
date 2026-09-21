# Gruppenthemen

Jede Gruppe entwickelt einen **eigenen ESP32-basierten Smart Sensor**. Zuerst entsteht ein funktionsfähiger **ESPHome-Prototyp**, danach eine eigene **Arduino-/FreeRTOS-Lösung**. Die konkrete Auswahl der Sensoren und Aktoren sowie die technische Detailplanung erfolgen durch die Gruppe und werden in M1/M2 begründet. Es werden daher keine bestimmten Sensormodelle, Produktnummern oder verbindlichen Bauteile vorgegeben.

Die allgemeinen Mindestanforderungen, Sicherheitsregeln und der Entwicklungsablauf stehen in [ASSIGNMENT.md](ASSIGNMENT.md). Jede Gruppe konkretisiert ihr Thema in [PROJECT.md](PROJECT.md), formuliert überprüfbare Anforderungen in [docs/requirements.md](docs/requirements.md) und dokumentiert die zugehörigen Prüfungen in [docs/testing.md](docs/testing.md).

## 1. Raumklima und CO₂

### Aufgabe und Ziel

Entwickelt ein System, das das Raumklima eines Klassenzimmers erfasst und bewertet. Mehrere fachlich sinnvolle Messgrößen sollen zu einem verständlichen Raumklima- beziehungsweise Lüftungszustand zusammengeführt werden.

### Was das System leisten soll

- Relevante Messwerte lokal erfassen, auf Gültigkeit prüfen und verarbeiten.
- Zeitliche Entwicklungen erkennen und daraus einen Trend oder Zustand ableiten.
- Messwerte und Zustände über MQTT bereitstellen sowie in Home Assistant und Grafana darstellen.
- Eine lokale oder zentrale Rückmeldung geben, wenn sich der Raumzustand verändert oder eine Handlung sinnvoll ist.

### Erwartetes Ergebnis

Ein funktionsfähiger Smart Sensor, der nicht nur Einzelwerte überträgt, sondern den Raumzustand nachvollziehbar bewertet und eine verständliche Lüftungs- oder Komfortinformation liefert.

### Besondere Grenzen/Hinweise

Die Gruppe entscheidet und begründet, welche Messgrößen für ein Klassenzimmer aussagekräftig sind. Die Bewertung darf sich nicht auf einen einzelnen Rohwert beschränken.

## 2. Smart-Uhr und Umgebungsstation

### Aufgabe und Ziel

Entwickelt ein eigenständiges Informationssystem, das Uhrzeit und ausgewählte Umgebungsinformationen erfasst, lokal verarbeitet und übersichtlich anzeigt. Die Anzeige soll als verständliche Raumstatusanzeige dienen.

### Was das System leisten soll

- Uhrzeit und ausgewählte Umgebungswerte zuverlässig bereitstellen.
- Aus Messwerten zusätzliche Informationen wie Zustände, Trends, Minimum/Maximum oder eine Komfortbewertung ableiten.
- Die wichtigsten Informationen lokal klar und gut lesbar anzeigen.
- Daten und Zustände über MQTT an Home Assistant und Grafana übertragen.

### Erwartetes Ergebnis

Eine eigenständig nutzbare Raumstatusanzeige, die aktuelle Informationen und abgeleitete Bewertungen verbindet und dieselben Daten auch im zentralen System bereitstellt.

### Besondere Grenzen/Hinweise

Das bloße Anzeigen von Uhrzeit und Rohwerten genügt nicht. Auswahl, Priorisierung und Darstellung der Informationen müssen begründet werden.

## 3. Anonyme Raumnutzung und Präsenzerkennung

### Aufgabe und Ziel

Entwickelt ein System, das anonym erkennt, ob und wie ein Raum genutzt wird, ohne einzelne Personen zu identifizieren.

### Was das System leisten soll

- Mehrere geeignete Beobachtungen erfassen und bei Bedarf kombinieren.
- Zustände wie `frei`, `Bewegung`, `belegt` oder `unklar` robust ableiten.
- Anwesenheitsdauer, Zustandswechsel und widersprüchliche Signale sinnvoll behandeln.
- Ergebnisse über MQTT bereitstellen und in Home Assistant sowie Grafana auswertbar machen.

### Erwartetes Ergebnis

Ein Smart Sensor, der aus anonymen Beobachtungen einen nachvollziehbaren Belegungszustand bildet und auch bei kurzzeitigen oder widersprüchlichen Signalen möglichst stabil reagiert.

### Besondere Grenzen/Hinweise

Es dürfen keine Personen identifiziert und keine personenbezogenen Anwesenheitslisten erstellt werden. Die Gruppe dokumentiert, wie Datenschutz und Fehlinterpretationen berücksichtigt werden.

## 4. Bluetooth-Präsenz mit ESPresense und Belegungsvalidierung

### Aufgabe und Ziel

Untersucht Bluetooth-basierte Präsenz- beziehungsweise Näheerkennung mit ESPresense. Die erkannten Zustände müssen verpflichtend mit einem selbst gebauten ESP32-Smart-Sensor und einer unabhängigen physischen Beobachtung kombiniert oder validiert werden.

### Was das System leisten soll

- Pseudonymisierte Bluetooth-Präsenzinformationen auswerten.
- Eine unabhängige physische Beobachtung mit eigener ESP32-Hardware erfassen.
- Signalstärkeschwankungen, Fehlzuordnungen und widersprüchliche Zustände erkennen und behandeln.
- Aus beiden Informationsquellen einen begründeten Belegungs- oder Vertrauenszustand ableiten.
- Ergebnisse über MQTT, Home Assistant und Grafana bereitstellen.

### Erwartetes Ergebnis

Ein Gesamtsystem, das zeigt, wie zuverlässig Bluetooth-Präsenz für eine Raumbelegung ist und wie die Aussage durch den eigenen Smart Sensor überprüft oder verbessert werden kann.

### Besondere Grenzen/Hinweise

Die reine Installation von ESPresense genügt nicht. Gerätekennungen müssen pseudonymisiert werden. Personenbezogene Anwesenheitskontrolle, Klarnamen und dauerhaft zuordenbare öffentliche Kennungen sind unzulässig.

## 5. Intelligente Beleuchtung

### Aufgabe und Ziel

Entwickelt ein System, das die Beleuchtungssituation im Raum erfasst, bewertet und entweder eine sichere Niederspannungsbeleuchtung geeignet ansteuert oder eine verständliche Handlungsempfehlung erzeugt.

### Was das System leisten soll

- Den aktuellen Beleuchtungsbedarf aus geeigneten Beobachtungen ableiten.
- Zeitliche Schwankungen berücksichtigen und hektisches Ein- und Ausschalten verhindern.
- Hysterese oder eine vergleichbare ruhige Regelstrategie einsetzen.
- Betriebszustand, Messwerte und Empfehlungen beziehungsweise Aktorzustände über MQTT, Home Assistant und Grafana bereitstellen.

### Erwartetes Ergebnis

Ein Smart Sensor mit stabiler Beleuchtungsbewertung und nachvollziehbarer Entscheidung, der eine sichere Demonstrationsbeleuchtung steuert oder eine klare Empfehlung ausgibt.

### Besondere Grenzen/Hinweise

Keine Eingriffe in Schulbeleuchtung, Leitungen, Jalousien oder feste Infrastruktur. Offene Arbeiten an Netzspannung sind verboten. Aktoren dürfen nur im sicheren Niederspannungsbereich und nach Freigabe eingesetzt werden.

## 6. Energie- und Heizungsüberwachung

### Aufgabe und Ziel

Entwickelt ein System, das Energieverbrauch und thermischen Zustand bewertet und unnötigen Verbrauch beziehungsweise ungünstige Betriebszustände erkennt.

### Was das System leisten soll

- Sicher erfassbare Informationen zu Energie und thermischem Zustand lokal verarbeiten.
- Zusammenhänge zwischen Temperatur, Raumnutzung, Fensterzustand, Heizung und Energie untersuchen, soweit dies mit eigener sicherer Hardware möglich ist.
- Trends, Auffälligkeiten oder ungünstige Betriebszustände ableiten.
- Ergebnisse über MQTT, Home Assistant und Grafana nachvollziehbar darstellen.

### Erwartetes Ergebnis

Ein Smart Sensor, der mindestens einen relevanten Energie- oder Heizungszustand verständlich bewertet und daraus eine begründete Warnung, Kennzahl oder Handlungsempfehlung erzeugt.

### Besondere Grenzen/Hinweise

Es dürfen ausschließlich berührungssichere beziehungsweise ausdrücklich freigegebene Schnittstellen verwendet werden. Offene Arbeiten an 230 V sowie Veränderungen der Schulheizung oder anderer Infrastruktur sind verboten.

## 7. Raumakustik und TTS-Ausgabe

### Aufgabe und Ziel

Entwickelt einen ESP32-Smart-Sensor, der den Lautstärkepegel lokal erfasst und bewertet. Zusätzlich verantwortet die Gruppe die sichere Einbindung des am Home-Assistant-Raspberry-Pi angeschlossenen Lautsprechers als zentralen TTS-Aktor.

### Was das System leisten soll

- Aus lokalen Pegelwerten einen verständlichen Akustikzustand ableiten.
- Trends, Spitzen und Zeitanteile in verschiedenen Zuständen berechnen.
- Pegelwerte und abgeleitete Zustände über MQTT, Home Assistant und Grafana bereitstellen.
- Die vorgegebene gruppenübergreifende TTS-Schnittstelle einrichten, validieren und dokumentieren.
- TTS-Anforderungen mit Quelle, Nachricht, Priorität und begrenzter Lautstärke sicher verarbeiten.

### Erwartetes Ergebnis

Ein Smart Sensor zur nachvollziehbaren Bewertung der Raumakustik sowie eine zentral nutzbare, kontrollierte TTS-Ausgabe über Home Assistant.

### Besondere Grenzen/Hinweise

Audioaufnahmen sind ausnahmslos verboten. Sprache und Roh-Audiodaten dürfen weder gespeichert noch übertragen werden; verarbeitet werden ausschließlich lokale Pegelwerte. Gruppen erhalten keinen direkten Shell-Zugriff auf den Raspberry Pi. TTS darf nur sachlich, verantwortungsvoll und mit begrenzter Lautstärke eingesetzt werden.

## 8. Wasser, Pflanzen und Gebäudezustand

### Aufgabe und Ziel

Entwickelt ein System, das einen sinnvollen Zustand aus dem Bereich Wasser, Pflanzenversorgung oder Gebäudezustand erkennt und bewertet.

### Was das System leisten soll

- Geeignete Zustandsgrößen lokal erfassen, prüfen und verarbeiten.
- Nicht nur einen Einzelwert übertragen, sondern beispielsweise Bedarf, Warnung, Trend, Leck-/Fehlerzustand oder Wartungsbedarf ableiten.
- Ergebnisse über MQTT, Home Assistant und Grafana bereitstellen.
- Optional eine sichere Niederspannungsaktion oder eine Warnanzeige auslösen.

### Erwartetes Ergebnis

Ein Smart Sensor, der einen praktisch relevanten Versorgungs-, Warn- oder Wartungszustand zuverlässig erkennt und verständlich darstellt.

### Besondere Grenzen/Hinweise

Wasserleitungen, Sanitäranlagen und feste Schulinfrastruktur dürfen nicht verändert werden. Ein möglicher Aktor muss im sicheren Niederspannungsbereich arbeiten und vor dem Einsatz freigegeben werden.

## Erwartete Ergebnisse aller Gruppen

Am Projektende weist jede Gruppe mindestens folgende Ergebnisse nachvollziehbar nach:

- ein vollständig ausgefülltes [PROJECT.md](PROJECT.md) mit begründeter Hardware- und Systemplanung,
- überprüfbare Anforderungen in [docs/requirements.md](docs/requirements.md),
- dokumentierte Architektur und ein klarer Datenfluss,
- einen funktionsfähigen ESPHome-Prototyp,
- eine eigene Arduino-/FreeRTOS-Lösung,
- MQTT Discovery und funktionsfähige Einbindung in Home Assistant,
- ein aussagekräftiges Grafana-Dashboard,
- dokumentierte Tests in [docs/testing.md](docs/testing.md),
- verständliche technische Dokumentation,
- die vollständige GitHub-Nachweiskette von der Anforderung über Issue, Branch, Commits, Pull Request und Review bis `Done`.

Die verbindlichen Mindestanforderungen und die Definition of Done stehen in [ASSIGNMENT.md](ASSIGNMENT.md) und gelten zusätzlich.
