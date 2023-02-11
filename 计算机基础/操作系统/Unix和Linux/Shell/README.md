# Shell

Linux 命令（Command） 和 Shell 内容。

* linux command
* shell

放在一起，主要是2者紧密联系。

## 学习指南

### 学习资料

* [图书][Linux命令行与shell脚本编程大全](http://product.dangdang.com/29417308.html)
* [图书][bash shell脚本编程经典实例](http://product.dangdang.com/29194781.html)
* [图书][Linux命令行与shell编程实战](http://product.dangdang.com/25578477.html)
* [图书][shell脚本实战](http://product.dangdang.com/26917928.html)
* [The Art of Command Line](https://github.com/jlevy/the-art-of-command-line)
  * Master the command line, in one page
  * [中文版](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)
* [Linux Command](https://github.com/jaywcjlove/linux-command)
  * Linux命令大全搜索工具，内容包含Linux命令手册、详解、学习、搜集

### 常用命令

#### 首字母目录

* [ [A](#a) | [B](#b) | [C](#c) | [D](#d) | [E](#e) | [F](#f) | [G](#g) | [H](#h) | [I](#i) | [J](#j) | [K](#k) | [L](#l) | [M](#m) | [N](#n) | [O](#o) | [P](#p) | [Q](#q) | [R](#r) | [S](#s) | [T](#t) | [U](#u) | [V](#v) | [W](#w) | [X](#x) | [Y](#y) | [Z](#z) ]

#### A

* ant
  * ant命令
* apt
  * 在 Debian 和 Ubuntu 中的 Shell 前端软件包管理器

#### B

* bash

#### C

* cat
  * 查看文件内容
* cd
  * 进入目录
* chmod
  * 修改文件权限
* chown
  * 修改文件所属
* clear
  * 清楚屏幕
* clock
  * 调整 RTC 时间
* convert
  * GraphicsMagick的工具命令
    * convert -font Hiragino  -fill grey -pointsize 50 -draw "text 1768,90 'AI记单词'" /Users/rollin/1-the.jpg
* cp
  * 复制命令
* crontab
  * 定时执行任务
* curl
  * 网络访问
  * 该命令可以用来测试网络情况访问情况，监控网页的响应时间等
    * curl -o /dev/test -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "http://127.0.0.1:8080/health"
    * curl -o /dev/test -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "https://www.baidu.com"
      * 0.004548::0.017515::0.130251::0.130386::5974.000
    * curl -o /dev/test -s -w %{time_namelookup}::%{time_connect}::%{time_starttransfer}::%{time_total}::%{speed_download}"\n" "https://www.xianglesong.com"
      * 0.005135::0.078192::0.327840::0.327971::10879.000

#### D

* date
  * 查看日期
* df -h /
  * 查看磁盘使用情况
* diff
* dig
  * 域名信息查看
* docker
  * docker命令工具
* du -sh \.
  * 返回当前目录使用空间

#### E

* expect
  * 很多时候要输入密码，可以借助于该工具，比如mysql，ssh登录等
    * mysql示例
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
  ```

#### F

* ffmepg
  * 视频相关命令
* find
  * 查找文件
  * find . -type d -name target -exec rm -fr "{}" \;
    * 批量强制删除文件夹
    * 一般删除java项目使用
  * find . -type d -name node_modules -exec rm -fr "{}" \;
    * 批量强制删除文件夹
    * 一般删除前端项目使用
  * find . -type d -empty -delete
    * 批量删除空文件夹
  * find . -name *.log -type f -delete
    * 批量删除文件
* firewall
  * 防火墙配置
* free
  * free -m
  * echo 1 > /proc/sys/vm/drop_caches
    * free pagecache
  * echo 2 > /proc/sys/vm/drop_caches
    * free dentries and inodes
  * echo 3 > /proc/sys/vm/drop_caches
    * free pagecache, dentries and inodes

#### G

* git
  * git工具命令
* grep
  * 正则查找文件（global search regular expression(RE) and print out the line）
  * grep "text" . -r -n
    * 在当前目录下搜索text，并递归查找子目录，输出字符串所在文件行数
    * grep "redis-server" . -rn
  * grep "text" test.sh
    * 在文件test.sh中搜索text
    * grep "text" test.sh -n
      * 在文件test.sh中搜索text，输出字符串所在文件行数
* groupadd
  * 用户组管理
* groupdel
  * 删除用户组
* groupmod
  * 修改用户组
* gunzip
  * 解压缩文件
* gzip
  * 压缩文件

* gradle
  * gradle命令

#### H

* history
  * 查看历史记录

#### I

* info
  * Read documentation in Info format
  * 阅读信息格式的文档
  * info ls
* iostat
  * 查看IO情况

#### J

* java
  * 执行java程序
* javac
  * 编译java代码，基本使用IDE了，一般不用
* jps
  * 查看java进程
* jstack
  * 检查java程序问题，类似的命令很多，参考官方说明

#### K

* kill
  * 删除进程
  * kill = kill -15
  * kill -2 = CTRL + C
  * kill -9 pid
  * kill -6
    * 产生dump文件
  * kill -l

    ``` text
    [root@apple ~]# kill -l
    1) SIGHUP	 2) SIGINT	 3) SIGQUIT	 4) SIGILL	 5) SIGTRAP
    2) SIGABRT	 7) SIGBUS	 8) SIGFPE	 9) SIGKILL	10) SIGUSR1
    3)  SIGSEGV	12) SIGUSR2	13) SIGPIPE	14) SIGALRM	15) SIGTERM
    4)  SIGSTKFLT	17) SIGCHLD	18) SIGCONT	19) SIGSTOP	20) SIGTSTP
    5)  SIGTTIN	22) SIGTTOU	23) SIGURG	24) SIGXCPU	25) SIGXFSZ
    6)  SIGVTALRM	27) SIGPROF	28) SIGWINCH	29) SIGIO	30) SIGPWR
    7)  SIGSYS	34) SIGRTMIN	35) SIGRTMIN+1	36) SIGRTMIN+2	37) SIGRTMIN+3
    8)  SIGRTMIN+4	39) SIGRTMIN+5	40) SIGRTMIN+6	41) SIGRTMIN+7	42) SIGRTMIN+8
    9)  SIGRTMIN+9	44) SIGRTMIN+10	45) SIGRTMIN+11	46) SIGRTMIN+12	47) SIGRTMIN+13
    10) SIGRTMIN+14	49) SIGRTMIN+15	50) SIGRTMAX-14	51) SIGRTMAX-13	52) SIGRTMAX-12
    11) SIGRTMAX-11	54) SIGRTMAX-10	55) SIGRTMAX-9	56) SIGRTMAX-8	57) SIGRTMAX-7
    12) SIGRTMAX-6	59) SIGRTMAX-5	60) SIGRTMAX-4	61) SIGRTMAX-3	62) SIGRTMAX-2
    13) SIGRTMAX-1	64) SIGRTMAX
    [root@apple ~]#
    ```

* killall
  * 杀死所有同名进程
  * killall java
    * 所有java启动进程都会被kill
* kubectl
  * k8s命令工具

#### L

* less
* locate
  * 查找文件
* ls
  * 列出当前目录内容
  * 常用ls -lrt
* lsof
  * list open files

#### M

* man
  * system's manual pager
  * 系统参考手册
    * [Linux manual page](https://man7.org/linux/man-pages/man1/man.1.html)
      * man ls
      * man man
      * man 1 man
      * man [section] ...
        * 1 Executable programs or shell commands
        * 2 System calls (functions provided by the kernel)
        * 3 Library calls (functions within program libraries)
        * 4 Special files (usually found in /dev)
        * 5 File formats and conventions, e.g. /etc/passwd
        * 6 Games
        * 7 Miscellaneous (including macro packages and conventions),
             e.g. man(7), groff(7), man-pages(7)
        * 8 System administration commands (usually only for root)
        * 9 Kernel routines [Non standard]
      * man 1 printf

        ```
        PRINTF(1)                 BSD General Commands Manual                PRINTF(1)

        NAME
            printf -- formatted output

        SYNOPSIS
            printf format [arguments ...]

        DESCRIPTION
            The printf utility formats and prints its arguments, after the first, under control of the format.  The format is a character string
            which contains three types of objects: plain characters, which are simply copied to standard output, character escape sequences which
        ```

      * man 3 printf

        ```

        PRINTF(3)                BSD Library Functions Manual                PRINTF(3)

        NAME
            printf, fprintf, sprintf, snprintf, asprintf, dprintf, vprintf, vfprintf, vsprintf, vsnprintf, vasprintf, vdprintf -- formatted out-
            put conversion

        LIBRARY
            Standard C Library (libc, -lc)

        SYNOPSIS
            #include <stdio.h>

        ```

* mkdir
  * 创建目录
* mv
  * 移动命令
* mvn
  * mvn命令
* mongo
  * mongodb命令工具
* more
* mount
  * 挂载
* mysql
  * mysql命令工具

#### N

* netstat
  * 查看网络情况
* nginx
  * nginx命令工具
* nohup
  * 非挂起运行程序
* npm
  * 前端包管理工具
* nslookup
  * 查看DNS记录

#### O

* open

#### P

* passwd
  * 修改密码
* ping
  * 测试网络是否可通
* pkill
  * pkill nginx
* ps
  * 查看进程
* pstree
  * 查看进程树
* pwd
  * 返回当前目录路径

#### Q

* quit

#### R

* reboot
  * 重启
* redis
  * redis-cli
  * redis-server
* rm
  * 删除文件
* rmdir
  * 删除目录
* rpm
  * rpm -qa | grep java

#### S

* scp
  * 传输文件
    * scp local_file
      * scp local_file remote_username@remote_ip:remote_folder
    * scp remote file
      * scp -P 4588 remote@remote_ip:/usr/local/sin.sh /home/administrator
    * [Linux scp命令](https://www.runoob.com/linux/linux-comm-scp.html)
* screen
  * 多重视窗管理程序
* service
  * 系统服务管理
* shutdown
  * 关闭
* sleep
  * 休息
* source
  * 读取并执行文件
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

* su
  * 切换用户
* sudo
  * 以系统管理者的身份执行指令
* supervisor
  * 监控工具
* sync
* systemctl
  * 为系统的启动和管理提供一套完整的解决方案
  * systemd
    * [精华][Systemd 入门教程：命令篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)

#### T

* tail
  * tail -f filename
* tar
  * 文件压缩和解压缩
* tcpdump
  * 抓包解包
* telnet
  * 远程登录工具
* top
  * 查看当前机器情况
* touch
  * 创建文件
* tree
  * 查看目录

#### U

* useradd
  * 添加用户
* userdel
  * 删除用户
* usermod
  * 修改账号
* unmount
  * 卸载
* unzip
  * 解压缩文件

#### V

* vi
  * 编辑文件

#### W

* who
  * 查看用户
  * w
* whoami
  * 查看当前用户
* wget
  * 下载工具

#### X

#### Y

* yarn
  * 又一个前端包管理工具
* yum
  * 在 Fedora 和 RedHat 以及 SUSE 中的 Shell 前端软件包管理器
  * yum search java | grep jdk

#### Z

* zip
  * 压缩文件

### 常见问题

* $0
  * 返回执行shell脚本的名称

  ``` shell
  > cat test.sh 
  #!/bin/bash

  echo "$0"

  > sh test.sh
  test.sh

  > ./test.sh
  ./test.sh
  ```

* $1
  * 返回对应位置参数

  ``` shell
  > cat test.sh 
  #!/bin/bash

  echo "$0"
  echo "$1"
  echo "$2"

  > sh test.sh a b c
  test.sh
  a
  b
  ```

* $?
  * is used to find the return value of the last executed command.
  * 返回上次命令执行的返回值，shell中一般0表示成功。

  ``` shell
  > cat test.sh 
  #!/bin/bash

  pwd
  echo $?

  ls test.txt
  echo $?

  > sh test.sh
  /Users/rollin/shell
  0
  ls: test.txt: No such file or directory
  1
  ```

* $$(2个$)
  * 指的是脚本运行的当前进行id号。
  
  ``` shell
  > cat test.sh
  #!/bin/bash

  echo $$
  sleep 10

  > sh test.sh
  85525

  ```

* $*
  * 所有参数，当有多个参数的时候，所有参数拼成一个长字符串作为一个参数
* $@
  * 所有参数，当有多个参数的时候，每个参数占用一个数组元素

  ``` shell
  > cat test.sh
  #!/bin/bash

  echo '$* ':"$*"
  echo '$@ ':"$@"

  echo "* show 1"
  for i in $*; do
      echo "$i"
  done

  echo "* show 2"
  for i in "$*"; do
      echo "$i"
  done

  echo "@ show"
  for i in "$@"; do
      echo "$i"
  done

  > sh test.sh a b c
  $* :a b c
  $@ :a b c
  * show 1
  a
  b
  c
  * show 2
  a b c
  @ show
  a
  b
  c
  ```

* $#
  * 参数的个数

  ``` shell
  > cat test.sh
  #!/bin/bash

  echo '$# ':"$#"

  > sh test.sh a b c
  3

  ```

* $!
  * 显示shell脚本中上一个后台执行命令的进程id号

  ``` shell
  > cat test.sh
  #!/bin/bash

  sleep 10 &
  echo '$!':$!
  sleep 10

  > sh test.sh &
  [1] 4470
  $!:4474    

  > ps -ef|grep sleep
  502  4474  4470   0  2:30下午 ttys001    0:00.01 sleep 10
  502  4476  4470   0  2:30下午 ttys001    0:00.01 sleep 10
  
  ```

* &&
  * means “AND”. And in command execution context like this, it means items to the left as well as right of && should be run in sequence in this case.
  * 表示常规的与操作。

* &
  * means that the preceding commands—to the immediate left of the &—should simply be run in the background.
  * 表示后台执行。

* \>&
  * is the syntax to redirect a stream to another file descriptor. echo test 1>&2 To redirect stdout to stderr.
  * 重定向标准输出到标准错误。

  * 0 is stdin, 标准输入
  * 1 is stdout, 标准输出
  * 2 is stderr, 标准错误

* /dev/null
  * is the null file. Anything written to it is discarded.
  * 表示空文件，任何输入会被丢弃。

### Shell编程

* shell脚本调试
  * sh -x ./script.sh

  ``` shell
    > cat test.sh
    #!/bin/bash

    echo "today is :"$(date +'%Y-%m-%d')

    > sh -x test.sh
    ++ date +%Y-%m-%d
    + echo 'today is :2023-02-10'
    today is :2023-02-10

  ```

  * 代码内部设置
  
  ``` shell
    > cat test.sh
    #!/bin/bash

    echo "start"
    set -x
    echo "today is :"$(date +'%Y-%m-%d')
    set +x
    echo "end"
    > sh test.sh
    start
    ++ date +%Y-%m-%d
    + echo 'today is :2023-02-10'
    today is :2023-02-10
    + set +x
    end

    ```
  
  * 文件开始标注

  ``` shell
    > cat test.sh
    #!/bin/sh -x

    echo "start"
    echo "today is :"$(date +'%Y-%m-%d')
    echo "end"
    > ./test.sh
    + echo start
    start
    ++ date +%Y-%m-%d
    + echo 'today is :2023-02-10'
    today is :2023-02-10
    + echo end
    end
  ```

* sh -v test.sh
  * 显示输出打印命令行的原始内容
  
  ``` shell
    > cat test.sh
    #!/bin/sh

    echo "today is :"$(date +'%Y-%m-%d')
    echo "end"
    > sh -v test.sh
    #!/bin/sh

    echo "today is :"$(date +'%Y-%m-%d')
    date +'%Y-%m-%d'
    today is :2023-02-10
    echo "end"
    end
  ```

#### 函数调用

* 函数调用

    ``` shell
      > cat func.sh
      
      #!/bin/bash

      datetime=$(date "+%Y-%m-%d %H:%M:%S")

      func() {
          echo "func $datetime"
      }

      func

      function loop_print() {
          count=0
          while [ $count -lt "$1" ]; do
              echo $count
              ((count++)) || true
              sleep 1
          done
          return 0
      }

      loop_print 3

      function func_params() {
          echo "$0"
          echo "$1"
          echo "$2"
          echo "$3"
          echo "$*"
          return 0
      }

      func_params 1 2 3 4 5

    ```

  ``` shell
    > sh func.sh   
    func 2023-02-11 08:57:51
    0
    1
    2
    func.sh
    1
    2
    3
    1 2 3 4 5
  ```

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
7. [Command Line Text Processing](https://github.com/learnbyexample/Command-line-text-processing)
8. [Linux manual page](https://man7.org/index.html)
