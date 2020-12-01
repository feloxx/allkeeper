# presto 启动停止

presto因为默认是不带集群上启动停止的操作，这里需要一个辅助脚本。

```bash
#!bash
##useage:
##-h:指定机器hostname，-c：指定（"start" or "stop" ）操作
##不加参数是默认启停所有机器presto
cmd="all"
function usage(){
  echo "命令可选参数：
        `basename $0` [-hhostname] [-c[start or stop]"
        exit
}
if [ $# -gt 0 ];then
  for i in $@
  do
    if  [[ $i == -h* ]];then
         h=${i#-h}
         [ $h ] || usage
    elif [[ $i == -c* ]];then
        cmd=${i#-c}
        [ ${cmd} ] || usage
    else
        usage
    fi
  done
fi

for host in `cat hosts`
do
  [ ${h} ] && [ ${h} != ${host} ] && continue
  echo "-------${host}"
  [ ${cmd} == "all" ] || [ ${cmd} == "stop" ] && ssh ${host} 'source /etc/profile;source /home/presto/.bash_profile;/opt/apps/presto-server-0.203/bin/launcher stop'
  [ ${cmd} == "all" ] || [ ${cmd} == "start" ] && ssh ${host} 'source /etc/profile;source /home/presto/.bash_profile;/opt/apps/presto-server-0.203/bin/launcher start'
  sleep 5
done
```