# concurrent

## 进程和线程

- 查看工具
- 运行原理(栈桢 上下文切换)

## 同步和异步

## java线程

- 创建方式
- 常见方法
  - start run
  - sleep yeild
  - join 同步，有时限、无时限
  - interrupte 打断标记：打断sleep wait join 、打断正常运行线程；两阶段终止模式；打断LockSupport.park,打断标记为真park失效
- 不推荐的方法(过时)
  - stop
  - suspend
  - resume
- Java 进程需要等待所有线程都运行结束，才会结束
- 非守护线程运行结束了，即使守护线程的代码没有执行完，也会强制结束

## 共享模型 管程

- 共享带来的问题。 多线程环境下对静态变量的自增、自减
- 互斥，synchronized 对象锁。语法，加在普通方法上，加在静态方法上。
- 线程安全分析。
  - 成员变量、静态变量。
    - 没有共享：线程安全
    - 有共享：只有读操作则线程安全，反之线程不安全。
  - 局部变量
    - 线程安全
    - 其引用的对象：引用对象没有逃离方法的作用范围则线程安全，反之线程不安全。（体现闭合原则）
  - 常见线程安全类：单个方法是原子的，方法的组合不一定是原子的
    - String
    - Integer
    - StringBuffer
    - Random
    - Vector
    - HashTable
    - JUC包下的类
  - 不可变类的设计，String / 无状态
    - replace、subString方法。
- synchronized
  - 偏向锁
    - 撤销偏向 revoke
    - 批量重偏向 bulk rebias
    - 批量撤销 bulk revoke
  - 轻量级锁
    - 锁膨胀 inflate
  - 重量级锁
- 锁消除 JIT 、锁粗化
- wait notify。 （Object的方法，获取锁时才能调用，配合synchronized）
- wait vs sleep。 wait释放锁，sleep不释放锁，放弃cpu；都是TIME_WAITING状态。
- 保护性暂停、生产者消费者
- LockSupport.park() unpark()
- java线程状态转换
