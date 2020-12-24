# presto监控指标

## 介绍

- presto 监控 （兼容prometheus grafana的jmx）
- preoto 长任务监控 （定时高频率5分钟或10分钟监控presto中产生的任务）
- presto 连接数 （Coordinator也是个RESTful接口，主要监控他的连接数）
- presto 任务数 （运行的，排队的）
- presto 节点数
- preost 用户行为监控 （presto的CLUSTER OVERVIEW页面，里的内容是实时的，需要对历史进行一个保存来完成其他的分析监控工作
  - 查询基本信息（状态，内存使用，总时间消耗，错误信息等）
  - 查询性能信息（每一步的时间消耗，数据输入输出量信息等）
  - 查询客户端参数信息（发起客户的基本信息，参数信息等）
  - 每个查询中所有stage的信息（输入输出量信息，内存使用情况，调用核的数量等）
  - 每个stage中所有task的信息（输入输出信息， 内存信息，调用核数等）
- presto split （监控split数，主要是防止用户提了产生大量split的SQL，而导致影响其他用户）
- presto 时间消耗 （监控所有sql的查询时间消耗）

## 指标讲解 与 运维对接

## 实现

## 参考