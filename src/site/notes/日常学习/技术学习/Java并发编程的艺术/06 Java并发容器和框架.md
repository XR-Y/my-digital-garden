---
{"dg-publish":true,"permalink":"/日常学习/技术学习/Java并发编程的艺术/06 Java并发容器和框架/","noteIcon":"1","created":"2023-07-25T10:15:55.353+08:00","updated":"2023-07-26T15:01:53.372+08:00"}
---


- Hashmap 线程不安全：并发执行 put 操作会导致 HashMap 的 Entry 链表成环，进而产生死循环获取 Entry。
- HashTable 效率低下：使用 synchronized 保证线程安全，但竞争激烈时效率低下，当某个线程在使用 put 方法添加元素时，其余线程不但不能使用 put 添加元素，通常也不能使用 get 获取元素。
- ConcurrentHashMap 锁分段：提高并发访问效率，解决 HashTable 所有访问线程竞争同一把锁的问题。
- ConcurrentHashMap 组成：Segment 数组结构和 HashEntry 数组结构组成，前者是可重入锁，后者存储键值对数据。
- 对元素 hashCode 再散列：减少散列冲突，使元素均匀分布在不同的 segment 中，从而提高元素存取效率。
- get 操作不需要加锁：需要使用的共享变量（统计当前 segment 大小的 count 字段和用于存储值的 HashEntry 的 value 字段）定义为 volatile 类型，对 volatile 字段的写入操作会先于读操作（happen before 原则）。
- put 操作：定位 Segment→ 判断是否需要扩容 → 定位添加元素位置，放入 HashEntry 数组中。
- 判断是否需要扩容：HashMap 在插入元素后判断，很可能之后没有新插入，相当于进行了无效扩容，因而 segment 在插入前判断扩容更恰当。
- 统计整个 concurrentHashMap 大小：首先尝试两次对所有 segment 的 count（volatile 变量）求和，如果 count 在这中途发生了变化，再采用全部加锁的方式求和统计。
- 判断统计过程中是否发生过变化：put、remove 和 clean 方法在操作前都会把变量 modCount 加一，因此统计前后比较 modCount 即可。
- ConcurrentLinkedQueue：基于链接节点的无界线程安全队列。
- HOPS 设计意图：tail 节点永远作尾节点实现简单清晰，但每次都需要使用循环 CAS 更新 tail 节点，入队效率低。因此仅当 tail 节点和尾节点距离大于等于常量 HOPS 的值（默认为 1）时才更新 tail 节点，但距离拉长带来的负面效果是每次入队定位尾节点耗费额外时间。但对 volatile 读操作开销远小于写操作，提升了入队效率。
- 出队操作：从队列里返回一个节点元素，并清空该节点对元素的引用。并不是每次出队都更新 head 节点，当 head 节点里有元素时，直接弹出其中元素，而不更新 head 节点。当 head 节点中没有元素时，才更新 head 节点。
- 阻塞队列：
  - ArrayBlockingQueue：数组结构组成的有界阻塞队列。
  - LinkedBlockingQueue：链表结构组成的无界阻塞队列。
  - PriorityBlockingQueue：支持优先级排序的无界阻塞队列。
  - DelayQueue：支持延时获取元素的无界阻塞队列，适用于缓存系统设计或定时任务调度等场景。
  - SynchronousQueue：一个不存储元素的阻塞队列，非常适合传递性场景，吞吐量大。
  - LinkedTransferQueue：一个由链表结构组成的无界阻塞队列，当前有消费者正在等待接收元素时可以将生产者传入的元素立即 transfer 过去。
  - LinkedBlockingDeque：一个由链表结构组成的双向阻塞队列。
- 工作窃取：某个线程从其他队列里窃取任务来执行，被窃取任务线程永远从双端队列头部拿任务执行，而窃取任务的线程永远从尾部拿任务执行。
  - 缺点：某些情况下依旧存在竞争，如双端队列中仅一个任务时，同时该算法消耗更多的系统资源，如创建更多线程和双端队列。
