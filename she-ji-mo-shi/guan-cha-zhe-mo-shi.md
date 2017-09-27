观察者模式：定义对象间一对多依赖关系，使得每当一个对象状态发生改变时，其相关依赖对象皆得到通知并被自动更新。

### Android中应用程序发送广播的过程

* 通过sendBroadcast把一个广播通过Binder发送给ActivityManagerService，ActivityManagerService根据这个广播的Action类型找到相应的广播接收器，然后把这个广播放进自己的消息队列中，就完成第一阶段对这个广播的异步分发。

* ActivityManagerService在消息循环中处理这个广播，并通过Binder机制把这个广播分发给注册的ReceiverDispatcher，ReceiverDispatcher把这个广播放进MainActivity所在线程的消息队列中，就完成第二阶段对这个广播的异步分发;

* ReceiverDispatcher的内部类Args在MainActivity所在的线程消息循环中处理这个广播，最终是将这个广播分发给所注册的BroadcastReceiver实例的onReceive函数进行处理。


