# RabbitMQ Federation介绍

标签（空格分隔）： RabbitMQ Linux


---
### 介绍
在非集群模式下不同的broker传递消息是federation插件的终极目标。几个原因：

- 松耦合
    Federation插件能够在不同的broker(cluster)之间传递消息。
        可以拥有不同的用户和虚拟主机
        可以运行不同的RabbitMQ、Erlang版本
- 广域网支持
    Fderation插件使用AMQP 0-9-1协议进行多broker通信，并支持断点重连。
- 自定义配置
    每个broker可拥有联合组件/本地组件， 你不必联合broker内所有组件。
- 灵活扩展
    Federation在不同的brokers之间不要求O(n^2)的连接。因此很容易扩展。

### 如何实现的？
    Federation插件允许用户为exchange和queue做联合。每个federated exchange 或者queue能够接收上游(upstreams, 位于另一个broker的远程exchange/queue)上的消息。federated exchange能够路由上游发布的消息到本地的队列上。 联合队列可以让本地的consumer消费来自上游队列的消息。
    Federation连接上游使用RabbitMQ Erlang Client. 因此可以指定vhost， 使用TLS、 多样的认证机制。
    获取更多细节，请参阅[federated exchanges][1] 和 [federated queues][2]。


  [1]: https://www.rabbitmq.com/federated-exchanges.html
  [2]: https://www.rabbitmq.com/federated-queues.html
