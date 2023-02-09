# Shell

## 学习指南

* [图书][Linux命令行与shell脚本编程大全](http://product.dangdang.com/29417308.html）
* [图书][bash shell脚本编程经典实例](http://product.dangdang.com/29194781.html）
* [图书][Linux命令行与shell编程实战](http://product.dangdang.com/25578477.html)
* [图书][shell脚本实战](http://product.dangdang.com/26917928.html)

### 常用命令

* pwd
  * 返回当前目录路径
* ls
  * 列出当前目录内容
  * 常用ls -lrt
* cd
  * 进入目录
* cp
  * 复制命令
* mv
  * 移动命令
* mkdir
  * 创建目录
* touch
  * 创建文件
* rm
  * 删除文件
* rmdir
  * 删除目录
* chmod
  * 修改文件权限
* chown
  * 修改文件所属
* vi
  * 编辑文件
* cat
  * 查看文件内容
* date
  * 查看日期
* clear
  * 清楚屏幕
* history
  * 查看历史记录
* df -h /
  * 查看磁盘使用情况
* du -sh \.
  * 返回当前目录使用空间
* top
  * 查看当前机器情况
* free
  * 查看内存使用情况
* netstat
  * 查看网络情况
* iostat
  * 查看IO情况
* tcpdump
  * 抓包解包
* curl
  * 网络访问
  * 该命令可以用来测试网络情况访问情况，监控网页的响应时间等
    * curl -o /dev/test -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "http://127.0.0.1:8080/health"
    * curl -o /dev/test -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "https://www.baidu.com"
      * 0.004548::0.017515::0.130251::0.130386::5974.000
    * curl -o /dev/test -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "https://www.xianglesong.com"
      * 0.005135::0.078192::0.327840::0.327971::10879.000

* ping
  * 测试网络是否可通
* telnet
  * 远程登录工具
* dig
  * 域名信息查看
* nslookup
  * 查看DNS记录
* wget
  * 下载工具
* supervisor
  * 监控工具
* crontab
  * 定时执行任务
* ssh
  * 远程登录工具
    * ssh -i  ~/certification/101_id_rsa root@192.168.1.101
    * ssh root@47.243.232.181
    * ssh免密登录操作步骤（3步）
      * 客户端生成公钥私钥对

        ``` shell
        > ssh-keygen
        ```

      * 发送id_rsa.pub到服务端机器上
  
        ``` shell
        > ssh-copy-id -i ~/.ssh/id_rsa.pub root@47.243.232.181
        ```

      * 验证

        ``` shell
        > ssh root@47.243.232.181
        # 上面的应该是等同于下面内容
        > ssh -i ~/.ssh/id_rsa root@47.243.232.181
        ```

    * [SSH原理与运用（一）：远程登录](http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html)
  * ssh远程登录并运行命令
  
  ``` shell
    ssh root@47.243.232.181 > /dev/null 2>&1 << eof
    cd /root
    touch abcdefg.txt
    exit
    eof
    echo done!
    done!
  ```

* nohup
  * 非挂起运行程序
* systemctl
  * 为系统的启动和管理提供一套完整的解决方案
  * systemd
    * [精华][Systemd 入门教程：命令篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
* firewall
  * 防火墙配置
* screen
  * 多重视窗管理程序
* service
  * 系统服务管理
* reboot
  * 重启
* shutdown
  * 关闭
* passwd
  * 修改密码
* useradd
  * 添加用户
* userdel
  * 删除用户
* usermod
  * 修改账号
* groupadd
  * 用户组管理
* groupdel
  * 删除用户组
* groupmod
  * 修改用户组
* mount
  * 挂载
* unmount
  * 卸载
* yum
  * 在 Fedora 和 RedHat 以及 SUSE 中的 Shell 前端软件包管理器
* apt
  * 在 Debian 和 Ubuntu 中的 Shell 前端软件包管理器
* find
  * 查找文件
* locate
  * 查找文件
* grep
  * 正则查找文件
* scp
  * 传输文件
    * scp local_file
      * scp local_file remote_username@remote_ip:remote_folder
    * scp remote file
      * scp -P 4588 remote@remote_ip:/usr/local/sin.sh /home/administrator
    * [Linux scp命令](https://www.runoob.com/linux/linux-comm-scp.html)
* tree
  * 查看目录
* sleep
  * 休息
* ps
  * 查看进程
* kill
  * 删除进程
  * kill = kill -15
  * kill -2 = CTRL + C
  * kill -9 pid
* killall
  * 杀死所有同名进程
  * killall java
    * 所有java启动进程都会被kill
* pkill
  * pkill nginx
* pstree
  * 查看进程树
* who
  * 查看用户
* whoami
  * 查看当前用户
* su
  * 切换用户
* sudo
  * 以系统管理者的身份执行指令
* clock
  * 调整 RTC 时间
* tar
  * 文件压缩和解压缩
* zip
  * 压缩文件
* unzip
  * 解压缩文件
* gzip
  * 压缩文件
* gznzip
  * 解压缩文件
* source
  * 读取并执行文件
* java
  * 执行java程序
* javac
  * 编译java代码，基本使用IDE了，一般不用
* jps
  * 查看java进程
* jstack
  * 检查java程序问题，类似的命令很多，参考官方说明
* mvn
  * mvn命令
* ant
  * ant命令
* gradle
  * gradle命令
* git
  * git工具命令
* docker
  * docker命令工具
* kubectl
  * k8s命令工具
* nginx
  * nginx命令工具
* mysql
  * mysql命令工具
* redis
  * redis-cli
  * redis-server
* mongo
  * mongodb命令工具
* ffmepg
  * 视频相关命令
* convert
  * GraphicsMagick的工具命令
    * convert -font Hiragino  -fill grey -pointsize 50 -draw "text 1768,90 'AI记单词'" /Users/rollin/1-the.jpg
* npm
  * 前端包管理工具
* yarn
  * 又一个前端包管理工具
* expect
  ./expect.sh

  ``` shell
      #!/usr/bin/expect

      # 首先安装好expect
      # yum install -y expect tcl tclx tcl-devel

      spawn mysql -h 127.0.0.1 -uroot -p
      set timeout 100
      expect "Enter password:"
      send "123456\r"
      interact
  ``` shell

### 常见问题

* $? is used to find the return value of the last executed command. 返回上次命令执行的返回值，shell中一般0表示成功。

* && means “AND”. And in command execution context like this, it means items to the left as well as right of && should be run in sequence in this case. 表示常规的与操作。

* & means that the preceding commands—to the immediate left of the &—should simply be run in the background. 表示后台执行。

* \>& is the syntax to redirect a stream to another file descriptor. echo test 1>&2 To redirect stdout to stderr. 重定向标准输出到标准错误。

  * 0 is stdin, 标准输入
  * 1 is stdout, 标准输出
  * 2 is stderr, 标准错误

* /dev/null is the null file. Anything written to it is discarded. 表示空文件，任何输入会被丢弃。

### 运维常用命令

#### 内存管理

* free
  * free -m
* sync
* echo 1 > /proc/sys/vm/drop_caches
  * free pagecache
* echo 2 > /proc/sys/vm/drop_caches
  * free dentries and inodes
* echo 3 > /proc/sys/vm/drop_caches
  * free pagecache, dentries and inodes

### 编程规范

* [google的shell编程规范](https://google.github.io/styleguide/shellguide.html)
* [google的shell编程规范中文版](https://zh-google-styleguide.readthedocs.io/en/latest/google-shell-styleguide/)

## Zsh

* [oh-my-zsh](https://ohmyz.sh)zsh能基本完美兼容bash的命令，并且使用起来更加优雅。
  * 我就用的是这个，不要太爽。
  * zsh读取的配置文件：~/.zshrc
  * 切换zsh：chsh -s /bin/zsh
  * 当从bash切换为zsh时，如果不想重新配置一遍.zshrc文件，可以__在.zshrc文件中加上source ~/.bash_profile，从而直接从.bash_profile文件读取配置
  * 打造自己的zsh terminal，mac下强热推荐，生产力工具，也赏心悦目，参考如下文章：
    * <https://blog.csdn.net/huihut/article/details/61418136>
    * <https://blog.csdn.net/scythe666/article/details/52003352>
    * <https://blog.csdn.net/successli1994/article/details/81746806>

* echo $SHELL
  * 查看当前使用shell
  * 切换bash： chsh -s /bin/bash
  * bash读取的配置文件：~/.bash_profile文件

## 参考文献

1. [https://linux.die.net/man/1/bash](https://linux.die.net/man/1/bash)
2. [Shell 输入/输出重定向](https://www.runoob.com/linux/linux-shell-io-redirections.html)
3. [Redirections](https://www.gnu.org/software/bash/manual/html_node/Redirections.html)
4. [Linux 命令大全](https://www.runoob.com/linux/linux-command-manual.html)
5. [OpenSSH Manual Pages](http://www.openssh.com/manual.html)
6. [Shell 传递参数](https://www.runoob.com/linux/linux-shell-passing-arguments.html)
