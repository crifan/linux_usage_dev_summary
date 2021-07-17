# 包管理器

## 注意事项

### 安装必要的依赖的包

如果需要编译安装，则除了要安装对应工具，还需要安装对应库的开发包，其中包括头文件等文件，是别的编译安装期间需要用到的

比如，Python3在编译安装期间，开启了`ssl`的时候，需要用到ssl的库：`openssl`

则除了要安装对应的库：

```bash
apt-get install openssl
```

之外，还要安装对应的头文件：

```bash
apt-get install libssl-dev
```

才能被正确编译
