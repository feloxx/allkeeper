# presto收集日常SQL

## 第一种方式 存入hive

**收集SQL**

目前的方式是通过客户端查询系统表`system.runtime.queries`实现

```
sqlcmd="select node_id,query_id,state,user,source,queued_time_ms,analysis_time_ms,distributed_planning_time_ms,created,started,last_heartbeat,\"end\",query from system.runtime.queries "
/opt/apps/presto-server-0.203/bin/presto --server http://presto地址:5797 --execute "$sqlcmd" > /tmp/presto.2020-01-01.data
```

**导入HIVE**

```
loadtohive()
{
  hive <<EOF
  set role admin;
  LOAD DATA LOCAL INPATH '装presto sql的目录' INTO TABLE 表 PARTITION(day='$day');
  EOF
}
```

**启动**

crontab中配置了个定时任务来执行

```
*/6 * * * *  . /etc/profile  ; sleep 30 ; 执行定时load脚本 2>&1
```