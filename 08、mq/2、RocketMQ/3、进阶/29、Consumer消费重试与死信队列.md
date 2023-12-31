## Consumer消费重试与死信队列



#### 什么是死信队列

消息重试达到最大次数，依然消费失败，则表示消费者在正常情况下无法正确的消费该消息，此时，RocketMQ不会立即把该消息丢弃，而是将其发送到该消费者对应的特殊队列中，这个队列就是死信队列，其中的消息则被称为死信消息。



#### 死信队列特征

1. 死信队列中的消息不会再被消费者正常消费
2. 死信消息存储有效期与正常消息相同，均为3天，3天后自动删除
3. 死信队列就是一个特殊的Topic，名称为%DLQ%consumerGroup@ConsumerGroup
4. 如果一个消费者组未产生死信消息，不会为其创建相应的死信队列



#### 一个消费者组中产生了死信的话，后果很严重！

如果产生死信，则证明consumerGroup中的消费者存在bug，需要查找原因，然后重新生产那些死信消息，重新消费。