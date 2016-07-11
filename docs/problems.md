###RabbitMQ运维过程中遇到的一些问题，以及解决方法

**`RabbitMQ Dashboard`或者`REST API`获取不到相关的统计信息**
````bash
$sudo rabbitmqctl eval 'application:stop(rabbitmq_management), application:start(rabbitmq_management).'
````
**意为重启状态统计数据库。**
- 参考链接：[@stackoverflow](http://stackoverflow.com/questions/7711528/rabbitmq-statistics-database-could-not-be-contacted-message-rates-and-queue-l)
