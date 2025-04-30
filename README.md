# DetectScan

A lightweight TCP port scan detection system based on Python. Ideal for attacker boxes, honeypots, or CTF red-team nodes.

---

## ✅ Features

- Real-time interface-level **SYN scan monitoring**
- Detect source IP and fingerprint scanning tools (e.g. **masscan**, **nmap**)
- **GeoIP lookup** and **Google Maps pin**
- Embedded **Discord alert notification**
- **Log auto cleanup** (retains 7 days)
- Language support: **中文 / English**

---

## 🔧 Install dependencies

```bash
sudo apt install tcpdump python3-requests
```

---

## 🔑 Setup Discord Webhook

Replace the `DISCORD_WEBHOOK` variable inside `ScanDetect.py` with your webhook URL:

```python
DISCORD_WEBHOOK = "https://discord.com/api/webhooks/your_webhook_here"
```

---

## 🚀 Run script manually

```bash

python3 ScanDetect.py

python3 ScanDetect.py --lang en
```

---

## ⚙️ Run automatically on system boot (systemd)

Create and edit a new systemd service:

```bash
sudo nano /etc/systemd/system/ScanDetect.service
```

Paste the following content:

```ini
[Unit]
Description=ScanDetect Service
After=network.target

[Service]
ExecStart=/usr/bin/python3 /usr/local/bin/ScanDetect.py
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Enable and start the service:

```bash
sudo systemctl daemon-reexec
sudo systemctl enableScanDetect.service
sudo systemctl start ScanDetect.service
```

---

## 🖼️ Sample Alert Output

```bash
🚨 [Scan Detected] IP: 192.168.1.99 | Tool: nmap | Region: Taiwan | Time: 2025-04-23 17:01:22
```
