# Nginx

## 学习指南

### Nginx安装

#### yum安装Nginx

```shell
# yum 安装
> yum install nginx
```

### 配置示例

#### Nginx环境

```text

[root@apple ~]# which nginx
/usr/sbin/nginx

[root@apple ~]# nginx -v
nginx version: nginx/1.20.1

[root@apple nginx]# nginx -V
nginx version: nginx/1.20.1
built by gcc 4.8.5 20150623 (Red Hat 4.8.5-44) (GCC)
built with OpenSSL 1.1.1k  FIPS 25 Mar 2021
TLS SNI support enabled
configure arguments: --prefix=/usr/share/nginx --sbin-path=/usr/sbin/nginx --modules-path=/usr/lib64/nginx/modules --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --http-client-body-temp-path=/var/lib/nginx/tmp/client_body --http-proxy-temp-path=/var/lib/nginx/tmp/proxy --http-fastcgi-temp-path=/var/lib/nginx/tmp/fastcgi --http-uwsgi-temp-path=/var/lib/nginx/tmp/uwsgi --http-scgi-temp-path=/var/lib/nginx/tmp/scgi --pid-path=/run/nginx.pid --lock-path=/run/lock/subsys/nginx --user=nginx --group=nginx --with-compat --with-debug --with-file-aio --with-google_perftools_module --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_degradation_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_mp4_module --with-http_perl_module=dynamic --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-http_xslt_module=dynamic --with-mail=dynamic --with-mail_ssl_module --with-pcre --with-pcre-jit --with-stream=dynamic --with-stream_ssl_module --with-stream_ssl_preread_module --with-threads --with-cc-opt='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -specs=/usr/lib/rpm/redhat/redhat-hardened-cc1 -m64 -mtune=generic' --with-ld-opt='-Wl,-z,relro -specs=/usr/lib/rpm/redhat/redhat-hardened-ld -Wl,-E'

[root@apple ~]# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

[root@apple ~]# service nginx status
Redirecting to /bin/systemctl status nginx.service
● nginx.service - The nginx HTTP and reverse proxy server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; vendor preset: disabled)
   Active: active (running) since 一 2022-12-05 09:49:56 CST; 2 months 0 days ago
 Main PID: 16859 (nginx)
   CGroup: /system.slice/nginx.service
           ├─16859 nginx: master process /usr/sbin/nginx
           └─16862 nginx: worker process

12月 05 09:49:56 apple systemd[1]: Starting The nginx HTTP and reverse proxy server...
12月 05 09:49:56 apple nginx[16854]: nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
12月 05 09:49:56 apple nginx[16854]: nginx: configuration file /etc/nginx/nginx.conf test is successful
12月 05 09:49:56 apple systemd[1]: Started The nginx HTTP and reverse proxy server.

[root@apple ~]# nginx -s reload

[root@apple ~]# ls /var/log/nginx/

[root@apple ~]# systemctl status nginx
● nginx.service - The nginx HTTP and reverse proxy server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; vendor preset: disabled)
   Active: active (running) since 二 2023-02-07 20:48:41 CST; 20h ago
 Main PID: 1240 (nginx)
   CGroup: /system.slice/nginx.service
           ├─1240 nginx: master process /usr/sbin/nginx
           └─1241 nginx: worker process

2月 07 20:48:41 apple systemd[1]: Starting The nginx HTTP and reverse proxy server...
2月 07 20:48:41 apple nginx[1235]: nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
2月 07 20:48:41 apple nginx[1235]: nginx: configuration file /etc/nginx/nginx.conf test is successful
2月 07 20:48:41 apple systemd[1]: Started The nginx HTTP and reverse proxy server.
```

#### 安装SSL证书

* aliyun给域名申请免费证书
  * <https://dc.console.aliyun.com/>

* 下载到服务器

``` text
    /usr/local/ssl/xianglesong/9236052_www.xianglesong.com.key
    /usr/local/ssl/xianglesong/9236052_www.xianglesong.com.pem
```

* 配置nginx

``` shell
# 查看nginx配置
> cat /etc/nginx.conf
```

``` text

worker_processes auto;
error_log /var/log/nginx/error.log;
pid /run/nginx.pid;

include /usr/share/nginx/modules/*.conf;

events {
    worker_connections 1024;
}

http {

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    include /etc/nginx/conf.d/*.conf;

    gzip on;
    gzip_comp_level 5;
    gzip_min_length 1k;
    gzip_buffers 4 16k;
    gzip_proxied any;
    gzip_vary on;
    gzip_types
    application/javascript
    application/x-javascript
    text/javascript
    text/css
    text/xml
    application/xhtml+xml
    application/xml
    application/atom+xml
    application/rdf+xml
    application/rss+xml
    application/geo+json
    application/json
    application/ld+json
    application/manifest+json
    application/x-web-app-manifest+json
    image/svg+xml
    text/x-cross-domain-policy;
    gzip_static on;
    gzip_disable "MSIE [1-6]\.";

    server {

      listen 80;
      listen 443 ssl;
      server_name www.rulinma.com;

      charset utf-8;
      access_log /var/log/nginx/rulinma.log;

      ssl_certificate /usr/local/ssl/rulinma/8919583_rulinma.com.pem;
      ssl_certificate_key /usr/local/ssl/rulinma/8919583_rulinma.com.key;
      ssl_session_timeout 5m;
      ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
      ssl_prefer_server_ciphers on;

      root  /usr/share/nginx/html/rulinma;
      location / {

      }

    }

    server {

      listen 80;
      listen 443 ssl;
      server_name www.xianglesong.com;

      charset utf-8;
      access_log /var/log/nginx/xianglesong.log;

      ssl_certificate /usr/local/ssl/xianglesong/9236052_www.xianglesong.com.pem;
      ssl_certificate_key /usr/local/ssl/xianglesong/9236052_www.xianglesong.com.key;
      ssl_session_timeout 5m;
      ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
      ssl_prefer_server_ciphers on;

      root  /usr/share/nginx/html/xianglesong;
      location / {
        index  index.html index.htm index.php;
        try_files $uri /index.html;
        add_header 'Access-Control-Allow-Origin' '*';
        add_header 'Access-Control-Allow-Credentials' 'true';
        add_header 'Access-Control-Allow-Methods' 'GET,HEAD,OPTIONS,POST,PUT';
        add_header 'Access-Control-Allow-Headers' '*';
      }

      location ~* .(css|js|png|jpg|jpeg|gif|gz|svg|mp4|ogg|ogv|webm|htc|xml|woff)$ {
        # 同上，通配所有以.css/.js/...结尾的请求
        access_log off;
        add_header    Cache-Control  max-age=360000;
      }

    }

    proxy_cache_path  /data/nginx/cache levels=1:2 keys_zone=nginx-cache:20m max_size=10g inactive=168h;
  
     server {

      listen 80;
      listen 443 ssl;
      server_name api.xianglesong.com;

      charset utf-8;
      access_log /var/log/nginx/api.log;


      ssl_certificate /usr/local/ssl/api/9236128_api.xianglesong.com.pem;
      ssl_certificate_key /usr/local/ssl/api/9236128_api.xianglesong.com.key;
      ssl_session_timeout 5m;
      ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
      ssl_prefer_server_ciphers on;

      location / {
        proxy_pass http://172.31.87.195:8081;

        add_header  Cache-Control  max-age=no-cache;
        
        proxy_cache nginx-cache;
        proxy_cache_valid 168h;

        proxy_ignore_headers Set-Cookie Cache-Control;
        proxy_hide_header Cache-Control;
        proxy_hide_header Set-Cookie;
      }

      location ~* /word/comment/comments$ {
        # 同上，通配所有以/word/comment结尾的请求
        proxy_pass http://172.31.87.195:8081;
      
        add_header  Cache-Control  max-age=no-cache;
        # 开启post缓存
        # proxy_cache_methods POST;
        # 考虑是评论，暂时不开启缓存
        # proxy_cache nginx-cache;
        # proxy_cache_valid 168h;
        # proxy_ignore_headers Set-Cookie Cache-Control;
        # proxy_hide_header Cache-Control;
        # proxy_hide_header Set-Cookie;
      }

    }

}


```

``` shell

# 配置修改后生效
[root@apple ~]# nginx -s reload

# 重启
[root@apple nginx]# service nginx restart
Redirecting to /bin/systemctl restart nginx.service

# 查看日志
[root@apple ~]# tail -f /var/log/nginx/error.log

# 查看端口，用来检查服务是否正常启动
[root@apple ~]# netstat -lntp
```

#### 后端的API的Nginx配置

```text
  server {

    listen 80;
    listen 443 ssl;
    server_name api.xianglesong.com;
    
    charset utf-8;
    access_log /var/log/nginx/api.log;

    ssl_certificate /usr/local/ssl/api/9234128_api.xianglesong.com.pem;
    ssl_certificate_key /usr/local/ssl/api/9234128_api.xianglesong.com.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;

    location / {
      proxy_pass http://172.32.12.192:8081;
    }

  }
```

#### Nginx启动

``` shell
  # 服务器nginx启动
  > service nginx start
```

#### Nginx开机自动重启

一般云厂商系统默认安装就有配置，设置命令启动即可。

``` text
  [root@apple ~]# cat /usr/lib/systemd/system/nginx.service
  [Unit]
  Description=The nginx HTTP and reverse proxy server
  After=network-online.target remote-fs.target nss-lookup.target
  Wants=network-online.target

  [Service]
  Type=forking
  PIDFile=/run/nginx.pid
  # Nginx will fail to start if /run/nginx.pid already exists but has the wrong
  # SELinux context. This might happen when running `nginx -t` from the cmdline.
  # https://bugzilla.redhat.com/show_bug.cgi?id=1268621
  ExecStartPre=/usr/bin/rm -f /run/nginx.pid
  ExecStartPre=/usr/sbin/nginx -t
  ExecStart=/usr/sbin/nginx
  ExecReload=/usr/sbin/nginx -s reload
  KillSignal=SIGQUIT
  TimeoutStopSec=5
  KillMode=process
  PrivateTmp=true

  [Install]
  WantedBy=multi-user.target
```

``` shell
  # 服务器nginx启动
  > systemctl enable nginx.service
    Created symlink from /etc/systemd/system/multi-user.target.wants/nginx.service to /usr/lib/systemd/system/nginx.service.
  > systemctl list-units --type=service
    nginx.service                      loaded active running The nginx HTTP and reverse proxy server
  > systemctl disable nginx.service
    Removed symlink /etc/systemd/system/multi-user.target.wants/nginx.service.
```

#### Nginx服务挂掉自动重启

``` shell
  [root@apple sh]# cat /lib/systemd/system/nginx.service
  [Unit]
  Description=The nginx HTTP and reverse proxy server
  After=network-online.target remote-fs.target nss-lookup.target
  Wants=network-online.target

  [Service]
  Type=forking
  PIDFile=/run/nginx.pid
  # Nginx will fail to start if /run/nginx.pid already exists but has the wrong
  # SELinux context. This might happen when running `nginx -t` from the cmdline.
  # https://bugzilla.redhat.com/show_bug.cgi?id=1268621
  ExecStartPre=/usr/bin/rm -f /run/nginx.pid
  ExecStartPre=/usr/sbin/nginx -t
  ExecStart=/usr/sbin/nginx
  ExecReload=/usr/sbin/nginx -s reload
  KillSignal=SIGQUIT
  TimeoutStopSec=5
  KillMode=process
  PrivateTmp=true
  # 添加下面2行挂掉自动重启
  Restart=always
  RestartSec=5

  [Install]
  WantedBy=multi-user.target
  [root@apple sh]#
```

``` shell
  # Nginx服务挂掉自动重启
  > systemctl daemon-reload
  > systemctl start nginx
```

#### Nginx服务挂掉通过监控脚本自动重启

##### 监控脚本

mon_nginx.sh

``` shell
  #!/bin/bash

  datetime=$(date "+%Y-%m-%d %H:%M:%S")

  # ! 直接运行命令
  if ! pgrep -x nginx &>/dev/null; then
      echo "At time:$(date) Nginx is stop." >>/var/log/nginx_messages
      service nginx start
  fi

  echo "end exec : " "$(basename "$0")" "${datetime}"

```

##### crontab定时

每分钟检测，进程不在则重启。

``` shell
[root@apple sh]# crontab -l

*/1 * * * * /app/xianglesong/timer/sh/mon_nginx.sh >> /data/backup/xianglesong/db/mon_nginx.log 2>&1

```

## 参考文献

1. [Nginx怎么实现https](https://cloud.tencent.com/developer/article/1514933)
2. [Nginx安装配置ssl模块支持https访问](https://blog.51cto.com/yang/2893940)
3. [SSL证书不会安装配置？手把手教会你，3步搞定](https://zhuanlan.zhihu.com/p/112317355)
4. [nginx使用ssl模块配置支持HTTPS访问](https://blog.csdn.net/duyusean/article/details/79348613)
5. [systemd设置nginx开机自启动](https://cloud.tencent.com/developer/article/1677940)
6. [如何在 Nginx 服务器中配置 GZip 压缩？](https://www.yaohaixiao.com/blog/how-to-configure-gzip-compression-with-nginx)
7. [网页GZIP压缩检测](https://tool.chinaz.com/Gzips)
   * curl -I -H"Accept-Encoding: gzip, deflate" "http://www.xianglesong.com"
8. [Nginx 缓存机制详解！](https://cloud.tencent.com/developer/article/1890195)
9. [Nginx配置前端http缓存](https://juejin.cn/post/7079601613135937550)
10. [【干货】前端Nginx统一配置](https://www.jianshu.com/p/e798adcdea8c)
11. [nginx缓存配置示例](https://lichi6174.github.io/nginx-cache)
12. [NGINX config generator on steroids](https://github.com/digitalocean/nginxconfig.io)
13. [Tengine](https://github.com/alibaba/tengine)
