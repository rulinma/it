# Zsh

马如林 ~/.zshrc 的内容，截取部分，仅供参考：

```shell

export ZSH=$HOME/.oh-my-zsh

#ZSH_THEME="robbyrussell"
ZSH_THEME="agnoster"

plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)

source $ZSH/oh-my-zsh.sh

JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home
JAVA_8_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_101.jdk/Contents/Home

export JAVA_8_HOME

ANT_HOME=/Users/rollin/tools/apache-ant-1.9.4
MAVEN_HOME=/Users/rollin/tools/apache-maven-3.3.1/
ANDROID_HOME=/Users/rollin/Library/Android/sdk/platform-tools:/Users/rollin/Library/Android/sdk/tools
GRADLE_HOME=/usr/local/Cellar/gradle/4.10.2

SONAR_RUNNER_HOME=/Users/rollin/tools/sonar-scanner-3.1.0.1141-macosx

export GMAGIC_HOME=/usr/local/GraphicsMagick
LD_LIBRARY_PATH=$GMAGICK_HOME/lib:$LD_LIBRARY
export PATH=$SONAR_RUNNER_HOME/bin:$JAVA_HOME/bin:$ANT_HOME/bin:$MAVEN_HOME/bin:$ANDROID_HOME:$GMAGIC_HOME/bin:$GRADLE_HOME/bin:$PATH
export LD_LIBRARY

DYLD_LIBRARY_PATH=/usr/local/mysql/lib:$DYLD_LIBRARY_PATH
export DYLD_LIBRARY_PATH

export PATH=$PATH:/usr/local/go/bin
export GOROOT=/usr/local/go
export PATH=$PATH:$GOPATH/bin

alias ssh_jump="ssh rollin@j2.rollin.net -p 2222"
alias ssh_j5="ssh rollin@j5.rollin.net -p 2222"
alias ssh_jp="ssh rollin@jbak.rollin.net -p 2222"
alias gs='git status '
alias ga='git add '
alias gb='git branch '
alias gc='git commit'
alias gd='git diff'
alias gk='gitk --all&'
alias gx='gitx --all'

MAGICK_HOME=/Users/rollin/tools/ImageMagick-7.0.10
export PATH=$PATH:/usr/local/mysql/bin:$MAGICK_HOME/bin
export DYLD_LIBRARY_PATH="$MAGICK_HOME/lib/"

export PATH="/usr/local/opt/ruby/bin:$PATH"

if [ `id -u` != '0' ]; then

  export VIRTUALENV_USE_DISTRIBUTE=1        # <-- Always use pip/distribute
  export WORKON_HOME=$HOME/.virtualenvs       # <-- Where all virtualenvs will be stored
  source /usr/local/bin/virtualenvwrapper.sh
  export PIP_VIRTUALENV_BASE=$WORKON_HOME
  export PIP_RESPECT_VIRTUALENV=true

fi

#source ~/.bash_profile

export NVM_DIR="/Users/rollin/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

```
