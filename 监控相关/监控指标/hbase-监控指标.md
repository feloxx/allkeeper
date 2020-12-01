# hbase监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

## 监控指标

- hbase 基础 （cpu、内存、存活节点、jmx、gc）
- 对接进程 namenode、datanode、journalnode、zkfc、zookeeper的存活监控
- 表 基础 （表的数量、大小、表的region数）

- HMaster 监控 （基础、存活、内存、gc）
  - 存活的RegionServer信息，时间和数量
  - 停止的RegionServer信息，时间和数量
  - 对接的zk信息
  - 正在merge的数量
  - 正在split的数量
  - 集群整体负载
  - 读写请求
  - 存活时间、启动时间

- RegionServer 监控（基础、存活、内存、gc）
  - 平均心跳延迟，各时间段心跳比例
  - region数量、大小
  - Region 副本本地化 比率
  - 读写请求
  - 缓存命中率
  - RPC太多了，暂时不列举
  - WAL 文件数量和大小
  - Memstore 大小
  - Store 数量 大小
  - split 请求 成功次数
  - mutation 数量 大小
  - 存活时间、启动时间

## 指标讲解 与 运维对接

## 实现

## 参考