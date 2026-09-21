# Home Assistant

Alle Smart Sensoren werden über den [verbindlichen MQTT-Standard](../docs/mqtt.md) und MQTT Discovery eingebunden. Projektspezifische Home-Assistant-Konfigurationen, Automatisierungen und Exporte werden hier dokumentiert.

Dokumentiert insbesondere:

- automatisch erkannte Geräte und Entitäten,
- Namen, Einheiten, Geräteklassen und stabile `unique_id`,
- Gerätezuordnung und Availability,
- relevante Automatisierungen,
- verwendete State-, Availability- und Command-Topics,
- Tests nach Start und MQTT-Wiederverbindung.

## Zentrale TTS-Ausgabe

Der Lautsprecher ist am selben Raspberry Pi wie Home Assistant angeschlossen. Home Assistant übernimmt die zentrale TTS-Ausgabe; Gruppe 7 betreut und dokumentiert diese Funktion.

Andere Gruppen senden ausschließlich validierte TTS-Anforderungen an `smartclassroom/shared/tts/request`. Die vollständige Payload mit `source`, `message`, `priority` und begrenzter `volume` ist im [MQTT-Standard](../docs/mqtt.md#6-tts-aktor-auf-dem-raspberry-pi) definiert.

Keine Gruppe erhält direkten Shell-Zugriff auf den Raspberry Pi. Keine Konfiguration oder Dokumentation darf Passwörter, Tokens, WLAN-Zugangsdaten oder andere Geheimnisse enthalten.
