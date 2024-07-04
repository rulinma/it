# Conda

[官网](https://conda.io/projects/conda/en/latest/index.html)

新手向导

* conda create -n <env-name>
* conda create -n myenvironment python numpy pandas
* conda info --envs
* conda activate myenvironment
* conda install matplotlib
* conda --version
* conda update conda

## 常用命令

* conda install --help
* conda create --name $ENVIRONMENT_NAME python
* conda activate $ENVIRONMENT_NAME
* conda deactivate
* conda info --envs
* conda search $SEARCH_TERM
* conda install --channel $URL $PACKAGE_NAME

### 实例

* conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
* conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
* conda config --set show_channel_urls yes
* conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
* conda create -n pytorch
* conda info --envs
* conda install pytorch torchvision torchaudio cpuonly -c pytorch

## 其它

conda-forge

## 参考文献

https://conda.io/projects/conda/en/latest/commands/index.html