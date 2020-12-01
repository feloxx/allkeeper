# spark监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

查资料得到是建议使用 官方的`graphite_exporter`来对接spark。

spark3.0后已经开始内置支持prometheus。目前有3种方式，`java agent`、`GraphiteSink和GraphiteExporter`、`Custom sink和Pushgateway server`

## 监控指标

- spark 基础 （实时监控各角色driver、executer等使用内存、CPU 和 存活节点、jmx、gc次数）
- spark 列表 （列表的方式显示正在运行的spark程序，主要显示该任务占用的cpu、内存、网络读写资源、启动时间、运行时间）
- spark driver （针对起的每个spark程序的driver实时监控，blockManager、DAG、jvm）
- spark executor （针对起的每个spark程序的executor实时监控，主要包括文件系统读写、线程、jvm）
- spark shuffle （针对起的每个spark程序的shuffle实时监控）

## 指标讲解 与 运维对接

## 实现

## 参考