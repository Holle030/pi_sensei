# pi-sensei – Technische Details & Fortschritte

Dieses Dokument ergänzt die `README.md` und enthält ausführliche Informationen zur Entwicklung, Konfiguration und aktuellen Status des Projekts.

---

## 🔧 Fortschritte der letzten Tage

### 1. SSH-Schlüsselbereitstellung

- Öffentliche und private SSH-Schlüssel wurden generiert und im `secrets/keys/`-Verzeichnis abgelegt.
- Die Datei `id_ed25519.pub` wurde dem Raspberry Pi hinzugefügt.
- Passwort-Authentifizierung wurde deaktiviert, um ausschließlich Schlüssel-basierte Anmeldung zu erlauben.

### 2. Python-Umgebung & Sensor-Setup

- Installation von Python 3 und `virtualenv` abgeschlossen.
- Virtuelle Umgebung für den BME280-Sensor erstellt.
- Folgende Pakete wurden erfolgreich installiert:
  - `adafruit-circuitpython-bme280`
  - `adafruit-blinka`
  - `RPI.GPIO`
- Sensor-Skript wurde vorbereitet, um Umweltdaten regelmäßig zu erfassen.

### 3. Fail2ban & Zeitsynchronisation

- Fail2ban konfiguriert, um SSH-Zugriffe zu überwachen und Angriffe zu blockieren.
- `systemd-timesyncd` aktiviert, um die Systemzeit zuverlässig zu synchronisieren.

### 4. WireGuard VPN-Konfiguration

- WireGuard installiert und konfiguriert.
- Schlüsselpaare für Server und Client im `secrets/keys/`-Verzeichnis abgelegt.
- Konfigurationsdateien (`wg0.conf.j2`, `pc-client.conf`) vorbereitet.
- VPN-Verbindung erfolgreich getestet.

### 5. Apache2 Webserver

- Apache2 installiert und konfiguriert.
- Webverzeichnis vorbereitet, um Sensordaten darzustellen.
- Platzhalter-HTML-Seite eingebunden, die später durch dynamische Sensordaten ersetzt wird.

### 6. BME280 Sensor & Web-Ausgabe

- Sensor erfolgreich initialisiert und liefert Messwerte.
- Problem festgestellt: Das Webupdate-Skript lädt die virtuelle Umgebung nicht korrekt.
  - Vermutlich liegt ein Pfadfehler oder ein fehlender Aktivierungsbefehl vor.
  - Fehlerbehebung steht noch aus.

---

## 🧪 Bekannte Probleme & To-Dos

- [ ] Sensor-Webupdate-Skript reparieren (virtuelle Umgebung korrekt laden)
- [ ] HTML-Ausgabe dynamisch gestalten (z. B. mit Flask oder einfachem CGI)
- [ ] Automatisierte Tests für Sensor-Skript einbauen
- [ ] Logging verbessern (z. B. mit `logging`-Modul statt `print`)
- [ ] Dokumentation für WireGuard-Client-Setup erweitern

---

## 🔐 Sicherheit & Vault

- Alle sensiblen Daten (Schlüssel, Konfigurationen) sind im `secrets/`-Verzeichnis gespeichert.
- Nutzung von **Ansible Vault** empfohlen:
  ```bash
  ansible-vault encrypt secrets/keys/server_private.key
