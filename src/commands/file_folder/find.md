# find

* `find`
  * 功能：查找字符串

## 用途举例

### Mac中统计代码行数

```bash
find . -name '*.md' | xargs wc -m
```

效果：可以统计出，每一个`md`文件的字符`character`个数，并且给出总数。

此方法，也适用于其他Linux类系统。
