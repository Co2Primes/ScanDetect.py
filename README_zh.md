# DetectScanPlus

基于 Python 的轻量级 TCP 端口扫描侦测系统。适用于攻击者机器、蜜罐或 CTF 红队节点。

---

## ✅ 功能特点

- 实时接口级 **SYN 扫描监控**
- 侦测来源 IP 与扫描工具特征（如 **masscan**、**nmap**）
- **GeoIP 地理位置查询** 与 **Google Maps 定位**
- 集成 **Discord 警报通知**
- **日志自动清理**（保留 7 天）
- 支援语言：**中文 / English**

---

## 🔧 安装依赖

```bash
sudo apt install tcpdump python3-requests
```

---

## 🔑 设置 Discord Webhook

请将 `ScanDetect.py` 中的 `DISCORD_WEBHOOK` 变量替换成你的 Discord webhook URL：

```python
DISCORD_WEBHOOK = "https://discord.com/api/webhooks/your_webhook_here"
```

---

## 🚀 手动运行脚本

```bash
# 中文模式（默认）
python3 ScanDetect.py

# 英文模式
python3 ScanDetect.py --lang en
```

---

## ⚙️ 开机自动运行（使用 systemd）

创建并编辑新的 systemd 服务文件：

```bash
sudo nano /etc/systemd/system/ScanDetect.service
```

粘贴以下内容：

```ini
[Unit]
Description=ScanDetect 服务
After=network.target

[Service]
ExecStart=/usr/bin/python3 /usr/local/bin/ScanDetect.py
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

启用并启动服务：

```bash
sudo systemctl daemon-reexec
sudo systemctl enable ScanDetect.service
sudo systemctl start ScanDetect.service
```

---

## 🖼️ 示例警报输出

```bash
🚨 [检测到扫描] IP: 192.168.1.99 | 工具: nmap | 地区: Taiwan | 时间: 2025-04-23 17:01:22
```
---
