# tail

查看文本文件的最末尾的内容，默认行数：`10`行

```bash
tail file_name
```

举例：

```bash
# tail uploadToOSS.py 
        logging.debug("averageProcessTime=%s", averageProcessTime)
    gSummaryInfo["processed"]["average"] = {
        "processTime": averageProcessTime,
        "fileSize": averageFileSize,
        "fileSizeStr": formatSize(averageFileSize),
    }


    saveJsonToFile(gSummaryInfoFullPath, gSummaryInfo)
    gSummaryInfoStr = jsonToPrettyStr(gSummaryInfo)
    logging.debug("gSummaryInfoStr=\n%s", gSummaryInfoStr)
```


如果要指定函数，用`-n`

```bash
tail -n 40
```
