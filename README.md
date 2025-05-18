```bash # auto-systemctl


nano /etc/systemd/system/pharos-bot.service

[Unit]
Description=Pharos Auto Bot Service

[Service]
Type=simple
ExecStart=/usr/bin/node /root/Pharos-Auto-Bot/index.js
WorkingDirectory=/root/Pharos-Auto-Bot
StandardOutput=append:/root/Pharos-Auto-Bot/bot.log
StandardError=append:/root/Pharos-Auto-Bot/bot.log


nano /etc/systemd/system/pharos-bot.timer

[Unit]
Description=Run Pharos Auto Bot every day at 14:40

[Timer]
OnCalendar=*-*-* 14:40:00
Persistent=true

[Install]
WantedBy=timers.target


sudo systemctl daemon-reload
sudo systemctl enable --now pharos-bot.timer


tail -n 30 /root/Pharos-Auto-Bot/bot.log
 sudo systemctl status pharos-bot.timer
