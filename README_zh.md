## ScanDetect.py
 一个基于 Python 的轻量级端口扫描侦测系统，适用于渗透测试主机、蜜罐、CTF 攻击端等场景。

## 功能特色

- ✅ 实时监听网卡 SYN 扫描行为
- ✅ 自动识别来源 IP、工具指纹（如 masscan、nmap）
- ✅ 地理位置查询 + Google 地图定位
- ✅ Discord 嵌入式告警推送
- ✅ 日志保存与 7 天自动清理
- ✅ 可选语言：中文 / English

## 使用方式

1. 安装依赖：
```bash
sudo apt install tcpdump python3-requests
---------------------------------------------------------
将 DISCORD_WEBHOOK 改为你自己的 Discord Webhook URL。
---------------------------------------------------------

2.执行脚本：
python3 DetectscanPlus.py        # 默认中文
python3 DetectscanPlus.py --lang en   # 英文模式
---------------------------------------------------------

3.开机自启动：
sudo nano /etc/systemd/system/DetectScanPlus.service

4.创建文件：
sudo nano /etc/systemd/system/DetectScanPlus.service

5.加入：
[Unit]
Description=DetectScanPlus Service
After=network.target

[Service]
Restart=on-failure

[Install]
WantedBy=multi-user.target
-------------------------------------------------------------

6.启用服务：
sudo systemctl daemon-reexec
sudo systemctl enable DetectScanPlus.service
sudo systemctl start DetectScanPlus.service

