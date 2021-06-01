---
title: "自定义GIT命令"
date: 2021-06-01T17:17:35+08:00
slug: 20210601151735
draft: true
---

使用 `Hugo` 和 `Github Pages` 搭建个人网站时，需要反复修改文件，删除旧输出，然后构建，最后发布。这一套操作太繁琐了,尝试下是否有其他方式可一直简化操作。

<!--more-->

## 如何简化操作

1. `git alias`
2. 自定义脚本文件

### 自定义脚本文件

```bash
#!/bin/sh

hugo --cleanDestinationDir && git add docs && git commit -m "update docs" && git push
```

<!-- TODO 待完善 -->