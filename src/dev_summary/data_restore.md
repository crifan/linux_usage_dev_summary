# 数据恢复

Linux中，万一不小心数据被删，借助相关数据恢复工具，也是有一定机会恢复误删数据的。

Linux中的数据被删恢复工具：

* `ext3grep`
  * 安装：
    * `sudo apt install ext3grep`
* `extundelete`
  * 能指定恢复单个文件
  * 支持系统格式：`ext3`、`ext4`
* 其他
  * `foremost`
    * 支持系统格式：`ext2`、 `ext3` 、`vfat`、`NTFS`、`ufs`、`jfs` 等
  * `debugfs`
