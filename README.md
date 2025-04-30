ScanDetect.py

A lightweight TCP port scan detection system based on Python, ideal for attacker boxes, honeypots, or CTF red-team nodes.
Features

    ✅ Real-time interface-level SYN scan monitoring
    ✅ Detect source IP and fingerprint scanning tools (e.g. masscan, nmap)
    ✅ GeoIP lookup and Google Maps pin
    ✅ Embedded Discord alert notification
    ✅ Log with auto cleanup (7 days)
    ✅ Language support: 中文 / English

Install dependencies:
sudo apt install tcpdump python3-requests

Replace DISCORD_WEBHOOK in the script with your own Discord Webhook URL.


Run script:
python3 DetectscanPlus.py         # Default: Chinese
python3 DetectscanPlus.py --lang en   # English mode


Run with systemd on boot:
sudo nano /etc/systemd/system/DetectScanPlus.service


Add the following:
[Unit]
Description=DetectScanPlus Service
After=network.target

[Service]
ExecStart=/usr/bin/python3 /usr/local/bin/DetectscanPlus.py
Restart=on-failure

[Install]
WantedBy=multi-user.target


enable it:
sudo systemctl daemon-reexec
sudo systemctl enable DetectScanPlus.service
sudo systemctl start DetectScanPlus.service

