# kafka监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

可以使用`kafka_exporter`来进行监控。并且grafana已经搭配了监控看板，使用`7589`官方id即可。

还有以下id可以参考

```
https://grafana.com/grafana/dashboards/7589 （推介）
https://grafana.com/grafana/dashboards/9018 （参考-新的）
https://grafana.com/grafana/dashboards/9947（参考-新的）
https://grafana.com/grafana/dashboards/10973（JMX-阿里云）
https://www.menina.cn/article/88
https://cloud.tencent.com/developer/news/377416
```

## 监控指标

- kafka 基础 （cpu、内存、存活节点、jmx、gc）
- broker 基础 （Log flush rate and time、broker数、leader副本数、分区数、下线分区数、速率）
- producer 基础 （总体生产速率）
- consumer 基础 （总体消费速率）
- topic 基础 （数量、分区、复制因子、速率）
- topic 偏移量/消费延迟 （实时监控每个topic 消费者组 偏移量情况 消费延迟情况）

## 指标讲解 与 运维对接

## 实现

## 参考





