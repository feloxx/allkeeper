# hive 启动停止

## 启动 hiveserver2

```
mv  /data1/hive/logs/hiveserver.log  /data1/hive/logs/hiveserver.log.bak
nohup hiveserver2 --hiveconf 你的配置 >> /data1/hive/logs/hiveserver.log 2>&1 &
```

## 启动 metastore

```
mv /data1/hive/logs/metastore.log /data1/hive/logs/metastore.log.bak
nohup $HIVE_HOME/bin/hive --service metastore > /data1/hive/logs/metastore.log 2>&1 &
```

## 整体停止

```
if [ $# -eq 1 ]
then
        tpye=$1
        if [ "$tpye" = "meta" ]
        then
                ps -ef|grep HiveMetaStore  |grep -v grep |awk '{print $2}' |xargs kill
        elif [ "$tpye" = "server" ]
        then
                ps -ef|grep org.apache.hive.service.server.HiveServer2 |grep -v grep |awk '{print $2}' |xargs kill
        else
                echo input  meta or server or null
                exit 1
        fi
else
        ps -ef|grep -E 'HiveMetaStore|org.apache.hive.service.server.HiveServer2' |grep -v grep |awk '{print $2}' |xargs  kill -9
fi
```

## 整体重启

```bash
#!/bin/bash

NOW_TIME=`date +%F" "%T`
DAY=`date +%F`
WORKDIR=$(cd `dirname $0`;pwd)

cd $WORKDIR
sh stop_hive.sh
sleep 3
hive_num=`sh pshive`
if [ "$hive_num" != "" ]
then
        echo " hive not stop... restop" >> $WORKDIR/restart.log.$DAY
        sh stop_hive.sh
        sleep 3
        pshive
else
        echo "hive stop success "
        echo "hive stop success " >> $WORKDIR/restart.log.$DAY
fi

nohup sh start-metastore.sh >/dev/null &
sleep 1
nohup sh start-hiveserver2.sh >/dev/null &
sleep 2
hive_num=`sh pshive`
if [ "$hive_num" = "" ]
then
        echo start hive failed !!!
        echo start hive failed !!! >> $WORKDIR/restart.log.$DAY
        pshive
else
        echo "hive start done"
        echo "hive start done"  >> $WORKDIR/restart.log.$DAY
fi
echo "sleep 5 check metastore"
sleep 5
res=`netstat -anp 2>/dev/null |grep -E '9083|10000' |grep LISTEN`
echo "$res"
echo "sleep 3 check hiveserver2 "
sleep 3
res=`netstat -anp 2>/dev/null |grep -E '9083|10000' |grep LISTEN`
echo "$res" >> $WORKDIR/restart.log.$DAY
echo "$res"
```