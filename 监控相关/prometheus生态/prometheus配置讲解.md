# prometheus配置讲解

1、Prometheus以scrape_interval规则周期性从监控目标上收集数据，然后将数据存储到本地存储上。

2、scrape_interval可以设定全局也可以设定单个metrics。

3、Prometheus以evaluation_interval规则周期性对告警规则做计算，然后更新告警状态。

4、evaluation_interval只有设定在全局。

- global：全局配置
- alerting：告警配置
- rule_files：告警规则
- scrape_configs：配置数据源，称为target，每个target用job_name命名。又分为静态配置和服务发现

```yaml
# 全局配置global:
  # 默认抓取周期，可用单位ms、smhdwy #设置每15s采集数据一次，默认1分钟
  [ scrape_interval: <duration> | default = 1m ]
  # 默认抓取超时
  [ scrape_timeout: <duration> | default = 10s ]
  # 估算规则的默认周期 # 每15秒计算一次规则。默认1分钟
  [ evaluation_interval: <duration> | default = 1m ]
  # 和外部系统（例如AlertManager）通信时为时间序列或者警情（Alert）强制添加的标签列表
  external_labels:
    [ <labelname>: <labelvalue> ... ]
 
# 规则文件列表
rule_files:
  [ - <filepath_glob> ... ]
 
# 抓取配置列表
scrape_configs:
  [ - <scrape_config> ... ]
 
# Alertmanager相关配置
alerting:
  alert_relabel_configs:
    [ - <relabel_config> ... ]
  alertmanagers:
    [ - <alertmanager_config> ... ]
 
# 远程读写特性相关的配置
remote_write:
  [ - <remote_write> ... ]
remote_read:
  [ - <remote_read> ... ]
```