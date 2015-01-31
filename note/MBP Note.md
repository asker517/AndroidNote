# Android Developing On Mac OS X(2014.12.09)

#### 1. Mac OS X 环境变量:

* /etc/profile (建议不修改这个文件,全局配置,不管是哪个用户,登录时都会读取该文件)
* /etc/bashrc (一般在这个文件中添加系统级环境变量, 全局配置, bash shell执行时, 不管是何种方式, 都会读取此文件)
* ~/.bash_profile (一般在这个文件中添加用户级环境变量)


#### 2. My ~/.bash_profile Example:

```
export ANDROID_HOME=/Users/Vincent/Android/android-sdk/
export PATH=${PATH}:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools

export GRADLE_HOME=/Users/Vincent/Android/gradle-2.2.1/
export PATH=$PATH:$GRADLE_HOME/bin

export ANT_HOME=/Users/Vincent/Android/apache-ant-1.9.4
export PATH=${PATH}:${ANT_HOME}/bin 

```