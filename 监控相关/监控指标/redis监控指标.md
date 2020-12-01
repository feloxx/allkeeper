# redis监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

redis_exporter使用的`https://github.com/oliver006/redis_exporter`

整体配置在ansible中，详情参考 roles中的 `redis` 和 `redis_exporter`

## 监控指标

该配置已经具有以下监控项

- 运行时长
- 内存占用
- 命令执行频率，命令调用频率
- 网络 I/O
- redis 每个db中的元素数量
- 过期key和未过期key比例

## 指标讲解 与 运维对接

## 实现

prometheus中添加的配置

```
  - job_name: 'redis_exporter_targets1'
    static_configs:
      - targets:
        - redis://10.100.12.36:6379
    metrics_path: /scrape
    relabel_configs:
      - source_labels: [__address__]
        target_label: __param_target
      - source_labels: [__param_target]
        target_label: instance
      - target_label: __address__
        replacement: 10.100.12.36:9121
  - job_name: 'redis_exporter1'
    static_configs:
      - targets:
        - 10.100.12.36:9121
```

## 参考

