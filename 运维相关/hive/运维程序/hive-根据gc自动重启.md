# hive 根据gc自动重启

判断日志里是否出现过gc，如果出现了则重启下hive。

```
WORKDIR=$(cd `dirname $0`;pwd)
#GC overhead limit exceeded
LogFile="/data1/hive/logs/metastore.log"

res=`grep "GC overhead limit exceeded" $LogFile`
TIME=`date +%F_%T`
if [ "$res" ]
then
        echo $TIME $res
        echo "$TIME restart hive metastore"
        sleep 1
        sh $WORKDIR/stop_hive.sh meta
        echo "stop hive metastore"
        sleep 5
        TIME=`date +%F_%T`
        ps -ef|grep 'HiveMetaStore' |grep -v grep
        sh $WORKDIR/start-metastore.sh
        echo "$TIME start hive metastore"
        ps -ef|grep 'HiveMetaStore' |grep -v grep
        sleep 5
        netstat -anp 2>/dev/null |grep -E '9083|10000' |grep LISTEN
else
        echo "$TIME nomarl"
fi
```
