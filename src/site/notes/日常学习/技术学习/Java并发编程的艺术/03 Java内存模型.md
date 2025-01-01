---
{"dg-publish":true,"permalink":"/日常学习/技术学习/Java并发编程的艺术/03 Java内存模型/","title":"03 Java内存模型","tags":["八股","Java并发"],"noteIcon":"1","created":"2023-07-17T11:11:22.552+08:00","updated":"2025-01-01T10:49:05.471+08:00"}
---


-   并发编程模型的关键问题：线程间通信和同步。
    -   通信是指线程间何种方式来交换信息，分共享内存（隐式）和消息传递（显式）两种，Java 并发采用的前者。
    -   同步是指程序中用于控制不同线程间操作发生相对顺序的机制。在共享内存中是显式进行的，需要显式指定线程间互斥执行的某个方法或某段代码。
-   重排序
    1.  编译器优化的重排序，不改变单线程程序语义。
    2.  指令级并行的重排序，重叠执行多条指令。
    3.  内存系统的重排序，基于缓存和读/写缓冲区。
    4.  1 属于编译器重排序，JMM 通过规则禁止部分编译器重排序；2 和 3 是处理器重排序，JMM 通过内存屏障指令来禁止特定类型的处理器重排序，以此避免内存可见性问题。
-   StoreLoad 内存屏障：具备其余三个屏障的效果，开销较大，通常需要刷新全缓冲区的数据到内存中。
-   happens-before：一个操作执行的结果需要对另一个操作可见。
    -   程序顺序规则：一个线程中的每个操作，happens-before 于该线程中的任意后续操作。
    -   监视器锁规则：对一个锁的解锁，happens-before 于对这个锁的加锁。
    -   volatile 变量规则：对一个 volatile 域的写，happens-before 于任意后续对这个 volatile 域的读。
    -   传递性：如果 A happens-before B，且 B happens-before C，那么 A happens-before C。
    -   start()规则：如果线程 A 执行操作 ThreadB.start()（启动线程 B），那么 A 线程的 ThreadB.start()操作 happens-before 于线程 B 的任意操作。
    -   join()规则：如果线程 A 执行操作 ThreadB.join()并成功返回，那么线程 B 中的任意操作 happens-before 于线程 A 从 ThreadB.join()操作成功返回。
-   as-if-serial 语义：不管怎么重排序，（单线程）程序的执行结果不能被改变。
-   控制依赖：影响指令序列执行的并行度，采用猜测执行克服该问题，处理器可以提前读取并计算结果，并将结果临时保存在称为重排序缓冲的硬件缓存中。
-   JMM 和顺序一致性模型的区别：
    -   顺序一致性模型保证单线程内的操作会按程序的顺序执行，JMM 则不保证，如正确同步的多线程程序在临界区内的重排序。
    -   顺序一致性模型保证所有线程只能看到一致的操作执行顺序，而在 JMM 中则不然，如写数据在线程本地内存中，刷新到主内存前，这个写操作仅对当前线程可见。
    -   顺序一致性模型保证对所有内存的读/写操作都具有原子性，而 JMM 不保证对 64 位的 long 型和 double 型变量的写操作具有原子性。在 32 位处理器上要求 64 位数据写具有原子性开销较大，因而该写操作可能被拆分为两个 32 位的写操作来执行，两个操作可能被分配到不同的总线事务，此时不具有原子性。
        -   任意读操作必须要在单个读事务中执行，不允许拆分。
-   volatile 特性：
    -   可见性：对一个 volatile 变量的读，总是能看到任意线程对这个 volatile 变量最后的写入。
    -   原子性：对任意单个 volatile 变量的读/写具有原子性，但多个 volatile 操作或类似 volatile++复合操作（分读入、累加和写入）不具有原子性。
-   volatile 重排序规则：
    -   当第一个操作是 volatile 读时，无论第二个操作是什么，都不能重排序。
    -   当第一个操作是 volatile 写，第二个操作是 volatile 读时，不能重排序。
    -   当第二个操作是 volatile 写时，无论第一个操作是什么，都不能重排序。
-   内存屏障插入策略总体保守，在确保正确性的情况下会根据实际方法执行细节和处理器内存模型重排序规则（如 X86 处理器仅对写-读操作做重排序）作优化，提高执行效率。
    -   在每个 volatile 写操作之前插入一个 StoreStore 屏障。
    -   在每个 volatile 写操作之后插入一个 StoreLoad 屏障。
    -   在每个 volatile 读操作之后插入一个 LoadLoad 屏障。
    -   在每个 volatile 读操作之后插入一个 LoadStore 屏障。
    -   在 X86 处理器中，volatile 写的开销通常比 volatile 读更大，因为执行 StoreLoad 屏障开销更高。
-   锁的内存语义：线程 A 释放锁，随后线程 B 获取这个锁，这个过程实质上是线程 A 通过主内存向线程 B 发送消息。
-   lock 前缀的作用：
    -   确保对内存的读-改-写操作原子执行，开始由总线锁定实现，开销大 ，后改为缓存锁定保证。
    -   禁止该指令，与之前和之后的读和写指令重排序。
    -   把写缓冲区中的所有数据刷新到内存中。
-   ReentrantLock：依赖于 Java 同步器框架 AbstractQueuedSynchronizer（FIFO 双端队列）。
    -   可重入：ReentrantLock 锁可以被同一线程多次获取。
    -   公平锁：首先读一个 volatile 变量`state`，释放时写该变量。
    -   非公平锁：首先用 CAS 更新 volatile 变量`state`，释放时写该变量。
-   写 final 域的重排序规则：
    -   JMM 禁止编译器把 final 域的写重排序到构造函数之外。
    -   编译器会在 final 域的写之后，构造函数 return 之前，插入一个 StoreStore 屏障。
    -   该规则可以确保，在对象引用为任意线程可见之前，对象的 final 域已经正确初始化，普通域则不具有该保障。
-   读 final 域的重排序规则：在读一个对象的 final 域之前，一定会先读这个 final 域对象的引用。编译器会在读 final 域操作的前面插入一个 LoadLoad 屏障。
-   X86 处理器不会对写-写重排序，也不会对存在间接依赖关系的操作重排序，因而在 X86 处理器下，final 域读/写不会插入任何内存屏障。
-   双重检查锁由来：下述方案 synchronized 性能开销过大。

```java
public class SafeLazyInitialization {
	private static Instance instance;
	public synchronized static Instance getInstance() {
		if(instance == null)
			instance = new Instance();
		return instance;
	}
}
```

-   双重检查锁定：规避 synchronized 开销，第一次检查不为 null 则不需要执行后续加锁和初始化操作。

```java
public class DoubleCheckedLocking {
	private static Instance instance;
	public static Instance getIntance() {
		if (instance == null) {
			synchronized (DoubleCheckedLocking.class) {
				if (instance == null)
					instance = new Instance();
			}
		}
		return instance;
	}
}
```

-   创建对象：分配对象的内存空间 → 初始化对象 → 设置 instance 指向刚分配的内存地址，后两步可能发生指令重排。
-   B 线程可能判断 instance 不为 null，接下来访问 instance 指向的对象，但该对象可能尚未完成初始化。
-   基于 volatile 的解决方案：声明 instance 为 volatile 变量，从而禁止初始化对象和设置 instance 指向刚分配的内存地址两步发生指令重排。
-   基于类初始化的解决方案（延迟初始化）：执行类的初始化期间，JVM 会去获取一个锁，这个锁可以同步多个线程对同一个类的初始化。

```java
public class InstanceFactory {
	private static class InstanceHolder {
		public static Instance instance = new Instance();
	}

	public static Instance getInstance() {
		return InstanceHolder.instance;
	}
}
```
