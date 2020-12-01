# hive 快速定位进程

```
#! /bin/bash

ps -ef | grep -E 'HiveMetaStore|org.apache.hive.service.server.HiveServer2' | grep -v grep
```