# canal-监控指标

## 监控指标简述

- canal 生产进程是否存活(对接mysql binlog的程序)
- canal 生产进程堆内存占用
- canal 消费进程是否存活(获得binlog中的数据后续操作逻辑的进程)
- canal 消费进程堆内存占用  
- canal 临时文件空间占用


- instance接收transactions计数
- instance基本信息
- instance订阅数量
- instance dump线程提交到异步解析队列过程中的阻塞时间(仅parallel解析模式)
- instance接收binlog字节数
- instance解析模式(是否开启parallel解析)
- instance client请求次数的计数
- 向instance client发送数据包字节计数
- 向instance client发送get接口的空结果计数
- instance client请求失败计数
- instance client请求的响应时间概况
- instance sink线程put数据至store的阻塞时间
- instance store接收到的events sequence number
- instance store成功消费的events sequence number
- instance store基本信息
- instance store接收到的所有events占用内存总量
- instance store成功消费的所有events占用内存总量
- store put操作完成的table rows
- client get请求返回的table rows
- client ack操作释放的table rows
- server与MySQL master的延时
- store put操作events的延时
- client get请求返回events的延时
- client ack操作释放events的延时

## 指标讲解 与 运维对接

## 实现

## 参考

- https://github.com/alibaba/canal/wiki/Prometheus-QuickStart
- https://blog.csdn.net/heaven_monkey/article/details/105664503
- https://www.cnblogs.com/dalianpai/p/14022235.html
- https://www.cnblogs.com/zh94/p/13937530.html