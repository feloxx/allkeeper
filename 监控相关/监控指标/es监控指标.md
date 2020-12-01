# es监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

es可以使用这个exporter `https://github.com/justwatchcom/elasticsearch_exporter/releases`

并且grafana已经搭配了监控看板，使用`2322`官方id即可。

## 监控指标

- es 基础 （cpu、内存、存活节点、jmx、gc）
- es 节点数
- es 分片 （活跃的主分片总数、活跃的分片总数（包括复制分片）、正在迁移的分片、正在初始化的分片、未分配的分片数）
- es 搜索 （query总数、时间，fetch总数、时间）
- es 索引 （索引数、二次刷新花费时间、总刷新花费时间）

## 指标讲解 与 运维对接

## 实现

## 参考

- https://www.cnblogs.com/caoweixiong/p/12156590.html