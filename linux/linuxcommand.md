#linux command.linux命令 

## 常用命令
command |  description
---|---
lsb_release -a <br/> uname -a| system info
getconf LONG_BIT| 查看系统位数；uname -a也能看出。
linuxInformation| [linuxInformation](/linux/linux-infomation.md)
whoami| 查看当前登录用户名
env| 查看当前环境
man ls| 一般 man命令查看 manual.
ssh [jiek]@[ip] -p [port]| ssh连接remote机器
useradd -d /home/[jiek] [jiek]| 添加用户
passwd [jiek]| 设置修改密码
scp -P (22) tmp.md [jiek]@[ip]/[home/jiek]:/home/jiek/| 把本地文件上传到远程服务器 ；注意 **-P、 ：**
ftp| 同scp
locale| 查看系统支持编码清单
vi /etc/sysconfig/i18n| 下存编码格式
cd -| 返回上次的目录
ctrl + r| （reverse-i-search）搜索并执行
netstat -an &#124; grep 端口号| 查看端口占用情况
telnet ip 443| 显示网络状态
lsof -i :22| 查看端口运行情况
sz|LINEX传windows（远端需要装上。`centos$ yum install lrzsz`; windows下使用）
rz|windows传到LINUX（远端需要装上。`centos$ yum install lrzsz`）
i=1; while [ $i -le 99 ]; do name=\`printf "scene_%02d.md"  $i\`; touch "$name"; i=$(($i+1)); done|while 循环执行
for i in $(seq 99); do name=$(printf scene_%02d.md $i); touch "$name"; done| for循环和seq命令

oh-my-zsh https://github.com/robbyrussell/oh-my-zsh
一个增强版shell工具

## download 下载模块
+ wget -O {outfilename} {url} #下载url存在指定目录的文件名

+ curl 访问地址的


## 上传
1. scp -v -P (22) tmp.md [jiek]@[ip]/[home/jiek]:/home/jiek/  
```
    把本地tmp.md上传到远程服务器 ；
    注意 1. -P接端口，默认22；2. 远程地址后的冒号，分割地址与目录**
    -v verbose mode 冗长模式
```
    
## install 安装
+ 安装 apt-get：
+ apt-get安装zsh > sudo apt-get install zsh
+ yum安装zsh > yum install zsh
+ brew

## compression 压缩
```command
$ tar -cvf a.tar folderOrFiles #把文件或目录打包，不压缩

$ tar -zcvf a.tar.gz folderOrFiles #打包并以gzip压缩

$ tar -jcvf a.tar.bz2 folderOrFiles #打包并以bzip2压缩

$ tar -ztvf a.tar.gz 查看tar.gz包中文件有哪些

$ tar -jtvf a.tar.bz2 查看tar.bz2包中文件有哪些

$ zip a.zip a.md #把a.md打包进a.zip > zip `-r` f.zip folder

$ rar
```

## decompression 解压
```command
.tar.gz  $ tar -zxvf **.tar.gz

.tar.bz2 $ tar -jxvf **.tar.bz2

.zip     $ unzip **.zip -d a/ # 加-t参数是验证包的完整性

.rar     $ unrar

.tar.xz  $ xz -d a.tar.xz  # 解压为.tar文件，> tar -xvf a.tar

$ unzip -l test.apk        #查看apk下的文件清单
```

##有用的一些东西

`$?`符号显示上一条命令的返回值，如果为0则代表执行成功，其他表示失败。
```command
if [[ $? -eq 0 ]];then
  echo success!
else
  echo fail!
fi
```

```command
$ ll `which java`   #输出java的列表目录内容,shell中`反逗号内为运行的命令

$ fpath=$(readlink -f .) && echo $fpath   ##获取文件的绝对路径； MAC下要安装`$ brew install coreunits`; `greadlink -f .`
```

以下为AndResGuard的实践示例简单shell
```command
#!/usr/bin/env bash
file=$1                    #获取第一个参数
if [ ! $file ]; then       #当此变更为空时
  file=input.apk
else 
java -jar AndResGuard-cli-1.1.16.jar $file -config config.xml -out outapk 
fi
```
