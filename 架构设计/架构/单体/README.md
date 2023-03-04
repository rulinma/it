# 单体

## 开机启动

### Java程序开机自动重启和失败重启

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

* systemctl daemon-reload
  * 重载所有服务
* systemctl enable word-world
  * 设置开机自启动
* systemctl is-enabled word-world
  * 查看开机启动状态
* systemctl status word-world
  * 查看服务状态
* systemctl start word-world
  * 启动 word-world
* systemctl stop word-world
  * 停止 word-world
* systemctl restart word-world
  * 重启 word-world
