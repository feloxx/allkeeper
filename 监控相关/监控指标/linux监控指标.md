# linux监控指标

> 只进行监控，后续产生的衍生操作请参阅 运维相关 中 各组件的 运维程序

## 介绍

主要使用`prometheus`提供的`node_exporter`。

直接沿用tidb中的node_exporter配置即可

## 监控指标

- Overview
  - Virtual CPUs
  - Total RAM
  - Total Swap
  - System Uptime
  - Node_exporter version
  - CPU、Memory、Swap Used
  - Load1、5、15
- Kernel
- CPU
- Memory
- Vmstat-Page
- Vmstat-Numa
- Vmstat-THP
- Vmstat-Compact
- Load
- Disk
- Filesystem
- Descriptors
- Network
- TCP
- PRocesses

## 指标讲解 与 运维对接

## 实现

## 参考