# 单体

## 开机启动

``` shell

> cat /etc/systemd/system/word-world.service

[Unit]
Description=word-world
After=network.target

[Service]
Type=forking
ExecStartPre=/usr/bin/sleep 30
ExecStart=/app/word-world/service/bin/start.sh start test >/dev/null 2>&1 &
ExecReload=/app/word-world/service/bin/start.sh restart test >/dev/null 2>&1 &
ExecStop=/app/word-world/service/bin/shutdown.sh
Restart=always
RestartSec=2
PrivateTmp=true

[Install]
WantedBy=multi-user.target

```
