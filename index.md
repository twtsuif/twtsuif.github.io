# Java Map

集合

Collection  元素孤立存在

Map  元素成对存在



HashMap

哈希表结构  key唯一 重写key的hashCode equals方法



LinkedHashMap

HashMap的子类  哈希表+链表   链表保证元素存取顺序一致

哈希表保证key唯一



Map接口定义的方法

put

remove

get

containsKey

keySet

entrySet



Entry

将键值对的对应关系封装为对象   键值对对象





### ConcurrentMap

### ConcurrentHashMap

HashMap的线程安全版本   数组+链表+红黑树

相比同样线程安全的HashTable  效率等方面极大提升







synchronized  内部实现：监视器锁  通过对象监视器  在对象头中的字段来表明

从旧版本到现在 已经很多优化  三种方式：偏向锁、轻量级锁、重量级锁

**偏向锁**：是指一段同步代码一直被一个线程访问，那么这个线程会自动获取锁，降低获取锁的代价。

**轻量级锁**：是指当锁是偏向锁时，被另一个线程所访问，偏向锁会升级为轻量级锁，这个线程会通过自旋的方式尝试获取锁，不会阻塞，提高性能。

**重量级锁**：是指当锁是轻量级锁时，当自旋的线程自旋了一定的次数后，还没有获取到锁，就会进入阻塞状态，该锁升级为重量级锁，重量级锁会使其他线程阻塞，性能降低。



CAS

Compare And Swap  乐观锁



volatile(非锁)

多个线程访问同一个变量   一个线程修改了这个值 其他线程能够立刻看到修改的值



分段锁

细化了锁的粒度 用在ConcurrentHashMap 实现高效的并发操作  操作不需要更新整个数组时 只锁数组中的一项就可以



ReentrantLock可重入锁

一个线程获取锁之后 再尝试获取锁时 自动获取锁    优点：避免死锁



HashTable

几乎所有的增删改都加了synchronized

synchronizedMap

使用对象锁保证多线程安全 本质也是对HashMap进行全表锁

ConcurrentHashMap

将HashMap切割 hash数组切分成小数组  小数组继承自ReentrantLock  

小数组名Segment  n个HashEntry



JDK1.7和1.8实现很不同  JDK1.8对HashMap进行了改造
