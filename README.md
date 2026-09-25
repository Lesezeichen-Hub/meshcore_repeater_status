# MeshCore Repeater Status

Versioniertes Lesezeichen-Hub-Modul und eigenständige Web-App für strukturierte Repeater-Statusabfragen über einen MeshCore-Companion. Repeater können lokal gespeichert und als JSON gesichert werden.

## Ablauf

1. Companion mit BLE-Firmware einschalten.
2. Handy/PC per Bluetooth verbinden.
3. Repeater auswählen.
4. Admin-Passwort des Repeaters eingeben.
5. **Status abfragen** drücken.
6. Die Anfrage läuft über das Mesh; Antwort oder Timeout wird angezeigt. Die BLE-Verbindung wird bei einem kurzen GATT-Abbruch automatisch wiederhergestellt.

Mit **Repeater speichern** bleibt ein Eintrag lokal im Browser erhalten. Über **Exportieren** entsteht eine JSON-Datei; **Importieren** übernimmt sie auf einem anderen Gerät.

Der Repeater braucht keinen Laptop vor Ort. Die Firmware verwendet den bestehenden MeshCore-Statusrequest `REQ_TYPE_GET_STATUS`; der Kanalbot ist nicht erforderlich.

## Start als eigenständige Web-App

Chrome oder Edge öffnen:

```powershell
python -m http.server 8000
```

Dann `http://localhost:8000` öffnen. Web Bluetooth funktioniert nur auf localhost, 127.0.0.1 oder HTTPS. Unter Android kann die Seite als PWA installiert werden.

## Lesezeichen-Hub

Den Ordner im Lesezeichen-Hub unter **Module** als lokales Modul auswählen. Die Version steht in `version.json` und folgt Semantic Versioning.

## Firmware

Der Repeater muss die normale Repeater-Firmware verwenden. Statusanfragen sind nur für authentifizierte Admin-Clients erlaubt. Standardmäßig lautet das lokale Testpasswort in diesem Fork `password`; produktiv sollte es geändert werden.
