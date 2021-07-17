# head

举例：

查看文本文件最开始的内容，默认行数：`10`行

```bash
head file_name
```

实际用途举例：

当文件改动后，去看文件最开头的几行的内容是否变化了：

```bash
# head uploadToOSS.py 
#!/usr/bin/env python
# -*- encoding: utf-8 -*-
# Function: Upload to OSS for course video(.mp4) & subtitle(.srt) & cover(.jpg)
#   Note:
#       1. also need update Mongod after upload OSS
#       2. video: before upload to OSS, need remove water mark
#       3. TODO: add support for user show
# Updated: 20190926


import time
```

->此处确认内容的确从

`Updated: 20190924`

变化为刚修改的：

`Updated: 20190926`



如果要制定输出的函数，用：`-n`

举例：

```bash
head -n 40
```

输出效果：

```bash
# tail -n 30 uploadToOSS.py 
    processCourseVideo()
    processAllVideoTime = calcTimeEnd("processAllVideo")
    logging.debug("processAllVideoTime=%s", processAllVideoTime)
    allVideoFileSize = getFileFolderSize(CourseRootFolder)
    logging.debug("allVideoFileSize=%s", allVideoFileSize)


    gSummaryInfo["all"] = gCurNum
    gSummaryInfo["processed"]["total"] = {
        "videoNum": gTotalVideoNum,
        "processTime": processAllVideoTime,
        "fileSize": allVideoFileSize,
        "fileSizeStr": formatSize(allVideoFileSize),
    }


    averageFileSize = 0
    averageProcessTime = 0.0
    if gTotalVideoNum > 0:
        averageFileSize = allVideoFileSize/gTotalVideoNum
        logging.debug("averageFileSize=%s", averageFileSize)
        averageProcessTime = processAllVideoTime/gTotalVideoNum
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
