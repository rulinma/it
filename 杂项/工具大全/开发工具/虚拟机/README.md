# 虚拟机

有几种，这里主要讲开源的Virtual Box。

## Virtual Box

* 安装前准备

  * [官网](https://www.virtualbox.org/)下载虚拟机，并安装
    * [6.1.42](https://www.virtualbox.org/wiki/Download_Old_Builds_6_1)
  * [CentOS](https://www.centos.org/)或其他官网下载iso文件，准备安装操作系统
    * 优先使用镜像下载，国内比较快些
    * [CentOS-7-x86_64-DVD-2009.iso](https://mirrors.aliyun.com/centos/7.9.2009/isos/x86_64/CentOS-7-x86_64-DVD-2009.iso)

* 安装过程
  * 新建虚拟机
  * 设置CPU，iso文件地址，磁盘大小，内存大小，网络配置
    * CPU个数2个
    * 磁盘40G，不要太小，否则不够扩容麻烦
    * 内存8G
    * 网络配置就选择桥接，选择你上网的网络，安装系统时候参考主机配置网络就可以，IP地址变最后一位即可
      * 使用桥接比较好的地方是有独立IP，虚拟机和主机可以相互通信，各虚拟机也可以相互通信

* 备注
  * 选择最小安装，比较快，后面按需安装
  * 可以不要图形用户界面，很多时候意义不大
    * 装了界面的，也可以无界面启动，在启动时候选择一下
  * 我一般习惯使用本地terminal ssh到虚拟机上操作
  * 导入导出进行备份和恢复
