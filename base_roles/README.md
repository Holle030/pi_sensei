# pi-sensei

Ein Ansible-Projekt zur automatisierten Konfiguration eines **Raspberry Pi 1** mit verschiedenen Diensten und Sensoren. Ziel ist es, den Pi als sicheren, sensorbasierten Mini-Server mit **WireGuard VPN**, **BME280-Sensor**, **Apache-Webserver** und weiteren Tools zu betreiben.

---

## 🧩 Projektübersicht

Dieses Projekt bietet eine vollständig automatisierte Lösung zur Konfiguration eines Raspberry Pi. Es umfasst:

- 🔐 **WireGuard VPN** – für sicheren Fernzugriff
- 🌡️ **BME280 Sensor** – misst Temperatur, Luftfeuchtigkeit und Luftdruck
- 🌐 **Apache2 Webserver** – zeigt Sensordaten auf einer Webseite an
- 🛡️ **Fail2ban** – schützt vor Brute-Force-Angriffen
- 🐍 **Python 3 & Virtualenv** – für das Sensor-Skript in isolierter Umgebung

---

## 📦 Anforderungen

- Raspberry Pi 1 oder vergleichbares Modell
- Debian-basierte Distribution (z. B. Raspbian)
- Ansible auf dem Steuer-PC
- SSH-Zugang zum Raspberry Pi

---

## 📁 Projektstruktur

```text
pi_sensei/
├── base_roles/
│   ├── handlers/
│   │   └── main.yml
│   ├── inventory/
│   │   └── inventory.ini
│   ├── main.yml
│   ├── README.md
│   ├── tasks/
│   │   ├── apache.yml
│   │   ├── bme280.yml
│   │   ├── firewall.yml
│   │   ├── hostname.yml
│   │   ├── main.yml
│   │   ├── python.yml
│   │   ├── ssh.yml
│   │   ├── systemtools.yml
│   │   ├── time.yml
│   │   ├── update_sensor_data.yml
│   │   └── wireguard.yml
│   ├── templates/
│   │   └── wg0.conf.j2
│   └── vars/
│       └── main.yml
├── secrets/
│   ├── configs/
│   │   └── pc-client.conf
│   └── keys/
│       ├── client_private.key
│       ├── client_public.key
│       ├── id_ed25519.pub
│       ├── server_private.key
│       └── server_public.key
└── site.yml
