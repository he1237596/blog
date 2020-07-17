---
date: 2018-01-10
categories: 
- linux
tags:
- linux
---
## 1、ls 命令 : 显示目录内容列表

Linux ls 命令用于显示指定工作目录下之内容（列出目前工作目录所含之文件及子目录)。

```
ls [-alrtAFR] [name...]
```

### 常用 options

- -a 显示所有文件及目录 (ls 内定将文件名或目录名称开头为"."的视为隐藏档，不会列出)
- -A 同 -a ,但不列出 "." (目前目录) 及 ".." (父目录)
- -R 若目录下有文件,则以下之文件亦皆依序列出



![ls-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXiciaz9GKQicnztPXBDQFSmP9EyO4FWMDQCibqDNKda9YwYpgU3uYgL6IU5Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## 2、rm 命令 : 删除文件/目录

Linux rm 命令用于删除一个文件或者目录。

```
rm [options] [name...]
```

### **options:**

- -i 删除前逐一询问确认
- -r 或-R：递归处理，将指定目录下的所有文件与子目录一并处理
- -f：强制删除文件或目录

![rm-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicd2E651EgurUmagE4Vr7klGbkVpwDpibKKTny4EYpO6LibYaT3r9guoCw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



![rm.png](https://mmbiz.qpic.cn/mmbiz_jpg/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicib6tZowDE15ZYaP1F8foz1iaZLvYUszZHaSBKRVPcSKcCTmtYCge1wsg/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

## 3、tail 命令 : 查看文件内容

tail 命令可用于查看文件的内容，有一个常用的参数 **-f** 常用于查阅正在改变的日志文件。

**tail -f filename** 会把 filename 文件里的最尾部的内容显示在屏幕上，并且不断刷新，只要 filename 更新就可以看到最新的文件内容。

```
tail [options][file]
```

### 常用 options:

- -f 循环读取

![tail-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicSOhBAQA8FGTWKE3Ria005nCGng9VEhAelb1rvAh6XNKdbzgYP7FFvfw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **4、mv 命令 : 文件移动/改名**

Linux mv 命令用来为文件或目录改名、或将文件或目录移入其它位置。

```
mv [options] source dest
# or
mv [options] source... directory
```

### **options:**

- -i: 若指定目录已有同名文件，则先询问是否覆盖旧文件
- -f: 在 mv 操作要覆盖某已有的目标文件时不给任何指示

![img](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicjzOovSAqeIGa3TzyOTNT8xnAkibk4h5NmfgE92n5KYpkCkJeOybnoyA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



![mv-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicwOH2HFDnz01jiaPz0GOkwOiaQL5WxTiaNAoibplP0ACx1NbcLj9DJkJIOg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **5、 touch 命令 : 新建文件**

Linux touch 命令用于修改文件或者目录的时间属性,包括存取时间和更改时间。若文件不存在,系统会建立一个新的文件。

ls -l 可以显示档案的时间记录。

```
touch [file]
```



![touch-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXiciaPibkLMu2vnR2ibq3wT4LdQicF8SzMp13WS9LBdPWicGg9ICDHiacXoMbgw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## 6、which 命令 : 查找文件

which 指令会在环境变量&dollar;PATH 设置的目录里查找符合条件的文件。

```
which [file...]
```



![which-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXichkcyiaogyuLb2mn0uuPrMx2IyiaFsYia6iaoSk1TAVGsjPTCqsjnTWprWA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## 7、cp 命令 : 复制文件/目录

Linux cp 命令主要用于复制文件或目录。

```
cp [options] source dest
# or
cp [options] source... directory
```

### 常用 options:

- -f：覆盖已经存在的目标文件而不给出提示。
- -r：若给出的源文件是一个目录文件,此时将复制该目录下所有的子目录和文件。



![cp-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXic1ALZfyfibz19SnwTmjVvXcaMyNZyk8ZHEeU4xiarfwiaMc66d8OsZEvzQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **8、cd 命令 : 切换工作目录**

Linux cd 命令用于切换当前工作目录至 dirName(目录参数)。

其中 dirName 表示法可为绝对路径或相对路径。若目录名称省略，则变换至使用者的 home 目录,"~" 也表示为 home 目录 的意思

```
cd [dirName]
```



![cd-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicMg3ichZZSibVqSNS4QkqiakvSGiaxswic0zu8G4yW0vfkTnt3o7mb8Gvia5A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **9、pwd 命令 : 显示工作目录**

Linux pwd 命令用于显示工作目录。

执行 pwd 指令可立刻得知您目前所在的工作目录的绝对路径名称。

```
pwd
```



![pwd-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicYOxfsbO9nXHuva5KzjMy2o92a02GEsF3SZPQqPFnPKRnVMUeicVrlEw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **10、 mkdir 命令 : 创建目录**

Linux mkdir 命令用于建立名称为 dirName 之子目录。

```
mkdir [-p] dirName
```

### **options**

- -p 确保目录名称存在,不存在的就建一个。



![mkdir-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicSiamgDAfeic1veWZR9yKtt7CC2P2V2BD1pV3hdrK6ZpcOQtItb4XkWeg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **11、 rmdir 命令 : 删除空目录**

Linux rmdir 命令删除空的目录。

```
rmdir [-p] dirName
```

### **options**

- -p 是当子目录被删除后使它也成为空目录的话,则顺便一并删除。



![rmdir-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicnzgdVKNpHPjeWeDMXQkqzukREibBRCwxic31B1P5r9VVRnr2PLTQAJcQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **12、cat 命令 : 查看文件内容**

cat 命令用于连接文件并打印到标准输出设备上。

```
cat fileName
```



![cat-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicUA0yuKeQ3VibumOYxO4AHfYrBuXDd2Bb8nsxtIzNusvSX1yTTNg5YtQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **13、ping 命令 : 检测主机**

执行 ping 指令会使用 ICMP 传输协议,发出要求回应的信息,若远端主机的网络功能没有问题,就会回应该信息,因而得知该主机运作正常。

```
ping [主机名称或IP地址]
```

### **常用 options:**

- -c<完成次数> 设置完成要求回应的次数。



![ping-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXico9aWR3iazkLTlBHkjrjxGEDLS4cb4Ae5zTeHHfAq0kggRAPnycAwnJg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **14、 telnet 命令 : 端口是否可访问**

虽然 Linux telnet 命令主要用于远端登入。执行 telnet 指令开启终端机阶段作业,并登入远端主机,

但是我更经常用它来查看某个远端主机端口是否可访问。

```
telnet [主机名称或IP地址<通信端口>]
```



![telnet-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicGJ14ldzEMk8lO4FwlH5ARdWePhgjqqPK63uobKMQ5y5mzpjgkYJM5g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **15、 grep 命令 : 查找关键字**

Linux grep 命令用于查找文件里符合条件的字符串。

```
grep [文件或目录...]
```



![grep-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicnmh4N0IBp0XoOFsNzxsonqicAg3dTic65icBlCUDWo7x5pW5sReJYcMLw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **16、ps 命令 : 显示当前进程状态**

Linux ps 命令用于显示当前进程 (process) 的状态。

```
ps [options]
```

### **常用 options**

- -e 显示所有进程。
- -f 全格式。


```
ps -ef # 显示所有命令，连带命令行
```

## **17、| 命令 : 管道命令**

通常情况下,我们只执行一条命令,那么如何执行多条命令呢？

管道是一种通信机制，通常用于进程间的通信（也可通过 socket 进行网络通信），它表现出来的形式将前面每一个进程的输出（stdout）直接作为下一个进程的输入（stdin）。

- 只能处理前一条指令的正确输出，不能处理错误输出
- 管道命令必须要能够接受来自前一个命令的数据成为 standard input 继续处理才行。



![pipe-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicW0JTROaSt4XmWED6uAo8jIicRJ2KsODuYib9BAiagafJWtDuoMaodHTTg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **18、 kill 命令 : 杀死进程**

Linux kill 命令用于删除执行中的程序或工作。

kill 可将指定的信息送至程序。预设的信息为 SIGTERM(15),可将指定程序终止。若仍无法终止该程序,可使用 SIGKILL(9)信息尝试强制删除程序。程序或工作的编号可利用 ps 指令或 jobs 指令查看。

```
kill [-s <信息名称或编号>][程序]　或　kill [-l <信息编号>]
```



![kill-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicIu4Rd9XzGelA6oRNVhHwpzVgInwDq2OQM2FlkJk8LkKg6y6ib10j8iag/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **19、 top 命令 : 实时显示进程动态**

Linux top 命令用于实时显示 process 的动态。

```
top
```

### **常用 options:**

- -pid 指定进程 id


```
top -pid 4712
```



![top-example.gif](https://mmbiz.qpic.cn/mmbiz_gif/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicgUyjGHMO81bZJWFzkGfKjU1yKkRE4LRdJWc5wjEDibKGl8XicHnnVicicw/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)



## **20、 clear 命令 : 清除屏幕**

Linux clear 命令用于清除屏幕。

```
clear
```

## **21、 alias 命令 : 别名配置**

Linux alias 命令用于设置指令的别名。

用户可利用 alias,自定指令的别名。若仅输入 alias,则可列出目前所有的别名设置。alias 的效力仅及于该次登入的操作。若要每次登入是即自动设好别名,可在.profile 或.cshrc 中设定指令的别名。

```
alias[别名]=[指令名称]
```

比如 git 原先就配置了一些别名,我们来看看



![alias-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicDCebapv4Ung862KZncdSVLlgN2A7V4LBxKpBUOEX8InGWMd3m0X1VQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **22、 find 命令 : 查找文件**

Linux find 命令用来在指定目录下查找文件。任何位于参数之前的字符串都将被视为欲查找的目录名。

如果使用该命令时,不设置任何参数,则 find 命令将在当前目录下查找子目录与文件。并且将查找到的子目录和文件全部进行显示。

```
find path -option [ -print ] [ -exec -ok command ] {} \;
```



![find-example.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicKicJpTCNiaxldgYS2lYYfsol4TjGFwaCp7OuBH7VP8zWlCic3nPlzBMUg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



## **23、 curl 命令 : 文件传输**

linux curl 是通过 url 语法在命令行下上传或下载文件的工具软件,它支持 http,https,ftp,ftps,telnet 等多种协议,常被用来抓取网页和监控 Web 服务器状态。

```
curl [options] [url]
```

### 常用 options:

- -o 把输出写到该文件中
- -I 仅仅返回 header

curl 命令能做很多事,用过的人都说香,我说说我常用的场景吧:

1. **调试请求**



![curl-example-1.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicVfatkjFFzNATRFc4zG6ykxXv3s2uFqc4MGnpU0vzuuH6FWibjqMnJLw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



1. **查看头部信息**



![curl-example-3.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicu5P8OI6nNACZ44b4IYkzs98Z0UpqMCfIiayz3N91GPibLRvvdNl3iafww/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



1. **抓取网页**



![curl-example-2.png](https://mmbiz.qpic.cn/mmbiz_png/eXCSRjyNYcaAWayNzE9hb4h7OEDttLXicw40UlPPblJYKicMjNVlicia17aBoJuIZncVAqpxmx774X4hdTEWfpucqA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)