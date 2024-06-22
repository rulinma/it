# Virtualenv

* 安装
  * pip install virtualenv

* 在当前目录下创建一个名为 myenv 的虚拟环境（使用默认 Python 版本）
  * virtualenv myenv

* 在当前目录下创建一个名为 myenv 的虚拟环境，并使用 Python 3.7 解释器
  * virtualenv -p /usr/bin/python3.7 myenv

* source <虚拟环境名称>/bin/activate
  * source myenv/bin/activate

* pip list

* pip install requests

* deactivate

# 参考文献

1. [virtualenv](https://virtualenv.pypa.io/en/latest/)