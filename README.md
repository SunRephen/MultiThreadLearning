# MultiThreadLearning
多线程学习资料

Object obj = new Object();
obj 对象引用栈 new Object()堆 对象元数据 oopInstanceDesc元数据(描述类结构,静态变量等)方法区。
http://www.hollischuang.com/wp-content/uploads/2017/12/20170615230126453.jpeg

同步方法 ACC_S...
同步代码块 monitor 对象内置锁 或 累锁(String.class etc).

1、同步方法通过ACC_SYNCHRONIZED关键字隐式的对方法进行加锁。当线程要执行的方法被标注上ACC_SYNCHRONIZED时，需要先获得锁才能执行该方法。《深入理解多线程（一）——Synchronized的实现原理》

2、同步代码块通过monitorenter和monitorexit执行来进行加锁。当线程执行到monitorenter的时候要先获得所锁，才能执行后面的方法。当线程执行到monitorexit的时候则要释放锁。《深入理解多线程（四）—— Moniter的实现原理》

3、在HotSpot虚拟机中，使用oop-klass模型来表示对象。每一个Java类，在被JVM加载的时候，JVM会给这个类创建一个instanceKlass，保存在方法区，用来在JVM层表示该Java类。当我们在Java代码中，使用new创建一个对象的时候，JVM会创建一个instanceOopDesc对象，这个对象中包含了对象头以及实例数据。《深入理解多线程（二）—— Java的对象模型》

4、对象头中主要包含了GC分代年龄、锁状态标记、哈希码、epoch等信息。对象的状态一共有五种，分别是无锁态、轻量级锁、重量级锁、GC标记和偏向锁。《深入理解多线程（三）—— Java的对象头》

偏向锁->轻量锁->膨胀->重量级锁(1.6以前都是重量级锁,内核和用户态切换消耗资源 synchorinzed性能低下的原因).
https://images2017.cnblogs.com/blog/1053518/201802/1053518-20180206155203420-628607348.jpg
