# 基础开发工具

此处介绍，Linux类系统中的开发工具集合库

Linux类系统中，如果后续需要源码编译等开发，往往需要安装一个开发包的集合：


* `Ubuntu`中叫做：`build-essential`
  * 解释
    * 中文直译：编译相关的基础的（工具，库等）
  * 如何安装：
    * `apt-get install build-essential`
* `CentOS`中叫做：`Development Tools`
  * 解释
    * 其中最核心的是这几个库：`gcc`、`gcc-c++`、`make`
      * 如何安装：`yum install gcc gcc-c++ make`
  * 如何安装：
    * `yum groupinstall "Development Tools"`
