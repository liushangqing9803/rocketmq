## Apache RocketMQ 21天学习源码
###第一天:搭建环境
###第二天：NameServer学习
####1、启动类
org.apache.rocketmq.namesrv.NamesrvStartup
1⃣️创建NamesrvConfig类和NettyServerConfig类，
namesrcConfig中包括:
1.rocketmq的主目录路径
2.kvConfig的路径
3.存储路径
4.环境名称
5.是否为集群测试
6.是否顺序消息
NettyServerConfig包括：
1、监听端口
2、线程数设置
3、缓存大小等
2⃣️命令行加载启动设置的配置文件-c，可以使用-h或-p
3⃣️处理日志信息
4⃣️启动方法
NamesrvController初始化，配置信息加载-》创建netty服务对象-》注册定时任务
1、每10秒扫描过期的broker，在120秒内没有上报心跳的broker
2、每10分钟打印kv信息
5⃣️注册钩子函数，在jvm退出是关闭数据controller的线程池和服务等


