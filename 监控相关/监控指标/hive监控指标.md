# hive监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

## 监控指标

- hive metastore连接数 （实时监控hive metastore连接数）
- hive metasotre守护 （实时监控hive metasotre进程，启停历史、jvm指标、文件描述符、Threads指标）
- hive server2连接数 （实时监控hive server2连接数）
- hive server2守护 （实时监控hive server2进程，启停历史、jvm指标、文件描述符、Threads指标）
- hive 模拟连接 （每天定时模拟用户来连接hive执行一个简单的sql，来判断hive是否可用）

---

- hive 表分区连续（每天定时检查hive所有表或指定表的分区是否连续，提供缺少数据的分区日期、链接）
- hive 同步（每天定时检查hive对应分区是否有数据，提供缺少数据的表）
- hive 表压缩 （每天定时检查所有表是否有进行压缩）
- hive 容量统计 （每天定时统计每个表的大小，借助grafana形式容量趋势统计、或者top10、top5）

---

- hive 表热点 （每天分析产生的sql，统计热点表top10、top5）
- hive 用户行为 （每天分析产生的sql，统计dml ddl操作，统计用户行为 top10、top5）

## 指标讲解 与 运维对接

## 实现

## 参考