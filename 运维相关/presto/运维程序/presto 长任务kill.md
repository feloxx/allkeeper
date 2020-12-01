# presto长任务kill

主要kill命令

通过调用presto客户端实现

```
/opt/apps/presto-server-0.203/bin/presto --server ip地址:5797 --execute "CALL system.runtime.kill_query(query_id => '$pid', message => 'Using too many resources')" 2>&1
```