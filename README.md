### 准备：

安装并启用syslog服务，做好对应日志级别（根据LOGGER函数中所使用的facility.severity）及权限的配置。

### 安装：

1. 将momosec\_bashrc放在/etc/下，权限修改为644，属组为root
2. 在/etc/bashrc中加载该文件，如[ -f /etc/momosec\_bashrc ] && . /etc/momosec\_bashrc


### 效果：

收集到的每条日志格式如下：

[syslog_part]: [ssh\_client\_ip] [server_name] [server_ip] [login_time] [ssh_pid] [tty] [login_user] [sudo_user] [pwd] [cmd]

- syslog_part：syslog服务添加的部分，具体内容由syslog配置决定
- ssh\_client\_ip：登录者IP，如从服务器A ssh登录到服务器B，则该项表示服务器A的IP
- server_name：命令执行时所在的服务器主机名
- server_ip：命令执行时所在的服务器IP
- login_time：命令执行者的登录时间
- ssh_pid：命令执行者的ssh进程号
- tty：命令执行者所处会话的tty
- login_user：命令执行者的ssh登录身份
- sudo_user：命令执行者的当前身份
- pwd：命令执行时所在的目录
- cmd：执行的命令，具体内容由history的格式决定

![example](https://github.com/momosecurity/cornerstone/raw/master/img/example.gif)

### 覆盖功能：

| 功能项 | 命令记录转发 | 
| ------------ |------------ |
|身份识别|✔︎|
|记录非交互式shell命令|✔︎|
|实时记录|✔︎|
|记录无tty下的命令|✔︎|
|记录sh命令|✔︎|
|记录脚本文件内执行的命令|✔︎|
|记录norc启动的shell命令|✔︎|
|是否方便数据的后续处理|✔︎|
|是否可以控制命令的执行|✘|
|非bash shell上执行的命令|✘|


### 关于我们
Website：[https://security.immomo.com](https://security.immomo.com)

WeChat:<br>
<img src="https://momo-mmsrc.oss-cn-hangzhou.aliyuncs.com/img-1c96a083-7392-3b72-8aec-bad201a6abab.jpeg" width="200" hegiht="200" align=center /><br>

[项目介绍](https://mp.weixin.qq.com/s?__biz=MzI2OTYzOTQzNw==&mid=2247484811&idx=1&sn=cd27473f6441d8b99da1b5f2f20a73bb&chksm=eadc0fe9ddab86ff21b191f53de79afea0f5063a978a76beefe641da95403e2fdf79c168488a&token=588906132&lang=zh_CN#rd)