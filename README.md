# Aria2 一键安装管理脚本 增强版(forked from P3TERX/aria2.sh) ＋ Install CaddyServer

# 1.P3TERX/aria2.sh
[![LICENSE](https://img.shields.io/github/license/P3TERX/aria2.sh?style=flat-square)](https://github.com/P3TERX/aria2.sh/blob/master/LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/P3TERX/aria2.sh.svg?style=flat-square&label=Stars&logo=github)](https://github.com/P3TERX/aria2.sh/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/P3TERX/aria2.sh.svg?style=flat-square&label=Forks&logo=github)](https://github.com/P3TERX/aria2.sh/fork)

Aria2 是目前最强大的全能型下载工具，它支持 BT、磁力、HTTP、FTP 等下载协议，常用做离线下载的服务端。Aria2 一键安装管理脚本是 Toyo (逗比) 大佬最为知名的脚本作品之一，2018年11月14日逗比大佬因未知原因突然失联。由于博主非常喜欢 Aria2 所以自2018年12月7日起开始接手这个项目并进行了大量的功能与细节优化，一直持续维护至今。增强版脚本整合了 [Aria2 完美配置](https://github.com/P3TERX/aria2.conf)，在安装 Aria2 的过程中会下载这套配置方案，这套方案包含了配置文件、附加功能脚本等文件，用于实现 Aria2 功能的增强和扩展，提升 Aria2 的下载速度与使用体验，解决 Aria2 在使用中遇到的 BT 下载无速度、文件残留占用磁盘空间、任务丢失、重复下载等问题。

## 项目地址

https://github.com/P3TERX/aria2.sh

支持项目请随手点个`star`，可以让更多的人发现、使用并受益。你的支持是我持续开发维护的动力。

## 系统要求

CentOS 6+ / Debian 6+ / Ubuntu 14.04+

## 架构支持

x86_64 / i386 / ARM64 / ARM32v7 / ARM32v6

## 使用说明

* 为了确保能正常使用，请先安装基础组件`wget`、`curl`、`ca-certificates`，以 Debian 为例子：
```
apt install wget curl ca-certificates
```

* 下载脚本
```
wget -N git.io/aria2.sh && chmod +x aria2.sh
```

* 运行脚本
```
./aria2.sh
```

* 选择你要执行的选项
```
 Aria2 一键安装管理脚本 增强版 [v2.6.2] by P3TERX.COM
 
  0. 升级脚本
 ———————————————————————
  1. 安装 Aria2
  2. 更新 Aria2
  3. 卸载 Aria2
 ———————————————————————
  4. 启动 Aria2
  5. 停止 Aria2
  6. 重启 Aria2
 ———————————————————————
  7. 修改 配置
  8. 查看 配置
  9. 查看 日志
 10. 清空 日志
 ———————————————————————
 11. 手动更新 BT-Tracker
 12. 自动更新 BT-Tracker
 ———————————————————————

 Aria2 状态: 已安装 | 已启动

 自动更新 BT-Tracker: 已开启

 请输入数字 [0-12]:
```

## 其他操作

启动：`/etc/init.d/aria2 start` | `service aria2 start`

停止：`/etc/init.d/aria2 stop` | `service aria2 stop`

重启：`/etc/init.d/aria2 restart` | `service aria2 restart`

查看状态：`/etc/init.d/aria2 status` | `service aria2 status`

配置文件路径：`/root/.aria2c/aria2.conf` （配置文件有中文注释，若语言设置有问题会导致中文乱码）

默认下载目录：`/root/downloads`

RPC 密钥：随机生成，可使用选项`7. 修改 配置文件`自定义

## 遇到问题如何处理

遇到问题先看 [FAQ](https://p3terx.com/archives/aria2_perfect_config-faq.html) 再提问，你还可以加入 [Aria2 TG 群](https://t.me/Aria2c)和小伙伴们一起讨论。要注意提问的方式和提供有用的信息，提问前建议去学习《[提问的智慧](https://github.com/ryanhanwu/How-To-Ask-Questions-The-Smart-Way/blob/master/README-zh_CN.md)》，这能更好的帮助你去解决问题和节约时间。诸如 “为什么不能使用？”、“那你能帮帮我吗？” 之类的问题应该没有人会知道。

</details>

## Lisence
[MIT](https://github.com/P3TERX/aria2.sh/blob/master/LICENSE) © Toyo x P3TERX

## 2.Install CaddyServer (Powered by doubi)
* CaddyServer一键安装脚本：
wget -N --no-check-certificate https://raw.githubusercontent.com/iiiiiii1/doubi/master/caddy_install.sh && chmod +x caddy_install.sh && bash caddy_install.sh
#备用地址
wget -N --no-check-certificate https://www.moerats.com/usr/shell/Caddy/caddy_install.sh && chmod +x caddy_install.sh && bash caddy_install.sh
```
* 安装Caddy成功后，继续新建一个虚拟主机文件夹
mkdir /usr/local/caddy/www
``````
* 使用IP进行访问：
echo ":80 {
 root /usr/local/caddy/www
 browse /Download
 timeouts none
 gzip
}" > /usr/local/caddy/Caddyfile
```
* 绑定指定域名：
* 重新写入配置到 Caddy 配置文件，注意下面这五行要一起复制粘贴！toyoo.pw 改成你自己的域名，然后去域名托管商解析你的域名即可
* 以下全部内容是一个整体，是一个命令，全部复制粘贴到SSH软件中并一起执行！
echo "http://toyoo.pw {
  root /usr/local/caddy/www
 browse /Download
  timeouts none
  gzip
}" > /usr/local/caddy/Caddyfile
```
* CentOS 系统：
yum install unzip -y
* Debian/Ubuntu 系统：
apt-get install unzip -y
```
* 然后继续：
* 新建Aria2下载文件夹 并进入文件夹
mkdir /usr/local/caddy/www/Download && cd /usr/local/caddy/www
 ```
* 下载并解压 AriaNg 文件，这段代码会自动检测并下载最新版本
Ver=$(wget --no-check-certificate -qO- https://api.github.com/repos/mayswind/AriaNg/releases/latest | grep -o '"tag_name": ".*"' | sed 's/"//g;s/tag_name: //g') && echo ${Ver}

* 如果上面自动检测最新版本的代码返回空白或者错误，那么请访问 https://github.com/mayswind/AriaNg/releases/latest 来查看最新版本号。
* 例如手动获取的版本号是 0.5.0，那么手动执行命令： Ver="0.5.0" ，然后继续下面步骤即可。
 
wget -N --no-check-certificate "https://github.com/mayswind/AriaNg/releases/download/${Ver}/AriaNg-${Ver}.zip" && unzip AriaNg-${Ver}.zip && rm -rf AriaNg-${Ver}.zip
 ```
* 赋予虚拟主机文件夹权限
chmod -R 755 /usr/local/caddy/www/
```
* 最后启动Caddy
/etc/init.d/caddy start
```
* Caddy其他命令：
启动：/etc/init.d/caddy start

停止：/etc/init.d/caddy stop

重启：/etc/init.d/caddy restart

查看状态：/etc/init.d/caddy status
```
## Lisence
moerats x doubi

## 本项目由个人整理！！！
