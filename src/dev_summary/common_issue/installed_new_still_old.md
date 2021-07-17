# 安装新版后使用仍是旧版

当安装了一个新的软件/库/工具后，虽然which查看到已经是新的，但是实际上运行该命令，使用该工具，则还是旧的，导致报错。

举例：

（1）Ubuntu中升级了pip3

```bash
pip3 install --upgrade pip
```

后，虽然

```bash
which pip3
```

已经是最新的版本：`/usr/local/bin/pip3`

但是实际上去运行pip3，结果还是用的旧的：`/usr/bin/pip3`

解决办法：重启shell终端 = 关闭旧的当前的shell，重新打开一个新的shell，即可

（2）基于Debian的树莓派中，用源码编译和安装了最新版Python 3.7.3

虽然

```bash
which python3
```

已经是新的`/usr/local/bin/python3`

且通过版本号可以确认的确是新版：

```bash
# python3 --version
Python 3.5.3
```

但实际运行的`python3`还是旧的版本：`/usr/bin/python3`

解决办法：重启shell终端，即可

(3) 在安卓上模拟Linux的Termux

```bash
pkg -y install wget
```

后，wget仍然是旧的

解决办法：

还要：

```bash
hash -r
```

-》目的：清除bash的缓存

-》命令行中找到的wget是最新的

-》wget就支持https地址了
