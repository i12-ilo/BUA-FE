### 库存归还

考虑如下问题：



1. 何时需要归还库存（Expired时间到达，顺手改变订单的状态 unpaid）



2. 谁来触发库存归还操作



### 触发归还操作

#### 主动轮询

##### 精度和性能

不够精准，如果为了精准需要缩短扫描轮询的间隔。

方式：定时器 和 扫描数据库

##### 定时器任务

Corntab、Timer（开一个新的线程）以及定时任务框架

#### 被动触发

模拟一个用户行为，当达到过期日期时会通知我们进行特殊操作。（归还库存或者状态变更）

#####  核心：延迟消息队列

区别于普通队列：当时间达到预期时，是队列主动通知我，而不是我想。。时，去队列里面主动取。

​									**主动返回**

## 延迟消息队列

提高系统并发的能力，只不过需要有针对性。 **消峰**

下单后 -> 成功 {短信、邮件、仓库调度。。。 同步变异步}

### RocketMQ

订单已过期，需要有一种机制能够通知到node业务层。

#### 安装

#### schedule



更可靠，更专业。

### 业务

#### 归还库存和优惠券

- nodejs配置Redis
- sendToRedis基本编写，以及预警时机（try catch）
- 接收键空间通知 -> onMessage，nodejs 配置
- 接收到通知的业务逻辑：
  - 归还优惠券
  - 归还库存

## RD

使用MQ

### 安装依赖，配置简单的express项目



