# Anforderungen – ausfüllbare Vorlage

Anforderungen müssen eindeutig, überprüfbar und mit Tests verknüpft sein. Verwendet ausschließlich das unten definierte `REQ-`-Schema, damit keine Verwechslung mit den Milestones M1–M6 entsteht.

## ID-Schema

- `REQ-F-01`, `REQ-F-02`, … für funktionale Anforderungen
- `REQ-NF-01`, `REQ-NF-02`, … für nichtfunktionale Anforderungen

## Funktionale Anforderungen

| ID | Priorität | überprüfbare Anforderung | geplante Prüfung |
|---|---|---|---|
| REQ-F-01 | Muss | Beispiel: Das Gerät veröffentlicht mindestens alle 10 Sekunden einen gültigen Messwert. | TEST-01 |
| REQ-F-02 | … | … | … |

## Nichtfunktionale Anforderungen

| ID | Priorität | überprüfbare Anforderung | geplante Prüfung |
|---|---|---|---|
| REQ-NF-01 | Muss | Beispiel: Das Gerät stellt nach einem MQTT-Ausfall die Verbindung selbstständig wieder her. | TEST-02 |
| REQ-NF-02 | … | … | … |

## Qualitätsregeln

- Jede Anforderung beschreibt ein Ergebnis, nicht nur eine Tätigkeit.
- Jede Muss-Anforderung besitzt mindestens einen zugeordneten Test in [testing.md](testing.md).
- Verwendet messbare Größen, Grenzen oder eindeutig beobachtbares Verhalten.
- Änderungen an Anforderungen werden über ein GitHub Issue und einen Pull Request durchgeführt.
