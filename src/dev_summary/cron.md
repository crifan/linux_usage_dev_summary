# cron

`cron`用来实现定时任务，其中的配置文件是`crontab`

* `cron`文件
  * root用户一般是
    * `/var/spool/cron`
      * 可以看到`crontab -l`列出的任务对应的原始文件配置
  * 系统级别的还有
    * `/etc/crontab`
    * `/etc/cron.d`下面的子文件

crontab相关命令：

* 列表当前任务
  * `crontab -l`
* 编辑任务
  * `crontab -e`
* 查看cron状态
  * `service cron status`
  * `/etc/init.d/cron status`
  * `ps -ef | grep cron`
    * 输出举例
      * `root    899   1 0 May07 ?    00:01:28 /usr/sbin/cron -f`
* 重启cron
  * `/etc/init.d/cron restart`
* 启动cron
  * `/etc/init.d/cron start`
* 查看cron的log日志：
  * `tailf /var/log/syslog | grep cron`

## cron文件格式(语法)

```bash
# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *   command to be executed
```

说明：

* 每一个域中，可以包含`*`或者`逗号`分割的数字，或者`-`连接的数字
  * `*`星号：表示任意
  * `,`逗号：分割表示时刻， separator
  * `-`短横线：连接，表示时间段， range of values
  * `/`斜杠：表示间隔， 如果第一个域为`/2`，则表示每隔两分钟， step value

举例：

```bash
例子：
# 每月的最后1天
0 0 L * * *


说明：

Linux
*    *    *    *    *
-    -    -    -    -
|    |    |    |    |
|    |    |    |    +----- day of week (0 - 7) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
|    |    |    +---------- month (1 - 12) OR jan,feb,mar,apr ...
|    |    +--------------- day of month (1 - 31)
|    +-------------------- hour (0 - 23)
+------------------------- minute (0 - 59)
```

以及：

| Field Name 字段 | Mandatory? 是否必填 | Allowed Values 允许值| Allowed special Characters 允许特殊字符 | 备注 |
| ---------- | ---------- | -------------- | -------------------------- | --- |
| Seconds | Yes | 0-59 | `,` `-` `*` `/` | 标准实现不支持此字段 |
| Minutes | Yes | 0-59 | `,` `-` `*` `/` | |
| Hours | Yes | 0-23 | `,` `-` `*` `/` | |
| Day of the Month | Yes | 1-31 | `,` `-` `*` `?` `/` `L` `W` | 只有部分软件实现了：`?` `L` `W` |
| Month | Yes | 1-12 or JAN-DEC | `,` `-` `*` `/` | |
| Day of the Week | Yes | 1-7 OR SUN-SAT | `,` `-` `*` `?` `/` `L` `#` | 只有部分软件实现了：`?` `L` `#` |
| Year | No | EMPTY, 1970-2099 | `,` `-` `*` `/` | 标准实现不支持此字段 |

说明：

* 标准字段
  * `逗号`：用于分隔列表。例如，在第5个字段(星期几)中使用 MON,WED,FRI 表示周一、周三和周五
  * `连字符`：定义范围。例如，2000-2010 表示2000年至2010年期间的每年，包括2000年和2010年
    * 除非用`反斜杠`=`\`转义，否则命令中的`百分号`=`%`会被替换成换行符，第一个百分号后面的所有数据都会作为标准输入发送给命令
* 非标准字段
  * `L`=`Last`
    * 当在星期几字段中使用的时候，可以指定给定月份的结构
      * 例如
        * `最后一个星期五``=`5L`
      * 在月日字段中，可以指定一个月的最后一天
  * `W`=`day of month`
    * 指定最接近给定日期的工作日（星期一-星期五）
      * 例如
        * `15W`=`最接近该月15日的工作日`
          * 所以
            * 如果15号是星期六，触发器在14号星期五触发
            * 如果15日是星期天，触发器在16日星期一触发。
            * 如果15号是星期二，那么它在15号星期二触发。
        * `1W`
          * 如果这个月的第一天是星期六，不会跨到上个月，触发器会在这个月的第三天（也就是星期一）触发。
      * 只有指定一天（不能是范围或列表）的时候，才能指定`W`字符
  * `#`=`星期几`
    * 后面必须跟一个介于`1`和`5`之间的数字。
      * 例如
        * `5#3`=每个月的第`三`个星期`五`
  * 在某些实现中，`?`用来代替`*`以将月中的某一天或周中的某一天留空
    * 其他cron的实现是替换`?`为cron守护进程的启动时间
      * 例如
        * `？？* * * *`
          * 如果cron在上午8:25启动，将更新为`25 8 * * * *`，并在每天的这个时间运行，直到再次重新启动
  * 分钟字段设置`*/5`表示每5分钟一次
    * 注意：这里指的是能被`5`整除的分钟数

特殊字符:

| Operator | Purpose | Example |
| -------- | ------- | ------- |
| asterisk `*`| Specifies all possible values for a field | An asterisk in the hour time field is equivalent to “every hour.” |
| question mark `?`| A question mark ( ? ) is allowed in the day-of-month and day-of-week fields. It is used to specify “no specific value,” which is useful when you need to specify something in one of these two fields, but not in the other. | If you want a trigger to fire on a particular day of the month (for example, the 10th), but you don't care what day of the week that is, enter 10 in the day-of-month field, and ? in the day-of-week field |
| dash `-` | Specifies a range of values | 2-5, which is equivalent to 2,3,4,5 |
| comma `,` | Specifies a list of values | 1,3,4,7,8 |
| slash `/` | Used to skip a given number of values | `*/3` in the hour time field is equivalent to 0,3,6,9,12,15,18,21. The asterisk `*` specifies `every hour`, but the `/3` means only the first, fourth, seventh. <br/>You can use a number in front of the slash to set the initial value. For example, `2/3` means 2,5,8,11, and so on. |
| `L` `last` | The `L` character is allowed for the day-of-month and day-of-week fields.<br/>Specifies either the last day of the month, or the last xxx day of the month. | The value L in the day-of-month field means “the last day of the month,” which is day 31 for January, or day 28 for February in non-leap years. If you use L in the day-of-week field by itself, it simply means 7 or SAT. But if you use it in the day-of-week field after another value, it means “the last xxx day of the month.” For example, 6L means “the last Friday of the month.”<br/>**HINT**:When you use the L option, be careful not to specify lists or ranges of values. Doing so causes confusing results. |
| `W` `weekday` | The W character is allowed for the day-of-month field. <br/>Specifies the weekday (Monday-Friday) nearest the given day. | If you specify 15W as the value for the day-of-month field, the meaning is “the nearest weekday to the 15th of the month.” So if the 15th is a Saturday, the trigger fires on Friday the 14th. If the 15th is a Sunday, the trigger fires on Monday the 16th. If the 15th is a Tuesday, it fires on Tuesday the 15th. However, if you specify 1W as the value for day-of-month, and the 1st is a Saturday, the trigger fires on Monday the 3rd, because it does not “jump” over the boundary of a month’s days. The W character can only be specified when the day-of-month is a single day, not a range or list of days.<br/>HINT:You can combine the L and Wcharacters for the day-of-month expression to yield LW, which translates to “last weekday of the month.” |
| pound sign `#` | The pound sign ( # ) character is allowed for the day-of-week field. This character is used to specify “the nth” xxx day of the month. | The value of 6#3 in the day-of-week field means the third Friday of the month (day 6 = Friday and #3 = the 3rd one in the month).<br/>**Other Examples**: 2#1 specifies the first Monday of the month and 4#5 specifies the fifth Wednesday of the month. However, if you specify #5 and there are fewer than 5 of the given day-of-week in the month, no firing occurs that month. |

## 在线工具

网上有些在线网站，可以帮助你计算和生成cron规则，比如

[crontab执行时间计算 - 在线工具](https://tool.lu/crontab/)

可以在线计算出cron规则的含义

举例：

cron规则是：

```bash
0 4 1 */2 0
```

当前时间：`2019-11-08 23:55`

网站会帮你计算出：

接下来7次的执行时间：

```bash
2019-12-01 04:00:00
2021-08-01 04:00:00
2023-10-01 04:00:00
2024-12-01 04:00:00
```

-》从而得知是：

之后每个偶数的月份的1号的04:00:00 去执行命令

频率是：每2个月一次

## 常见问题

### 命令本身运行没问题，但cron执行任务不执行不起效果

```bash
sudo sh /root/xxx-ssl/renew_cert.sh
```

虽然命令单独执行没问题，但是cron不执行任务，不起效，则可能是脚本权限问题

解决办法：

需要加上可执行权限

```bash
chmod +x /root/cy-ssl/renew_cert.sh
```

才可以。

