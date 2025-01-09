## 第二章 

11.简述系统调用的实现过程

![image-20241221125521380](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221125521380.png)

12.简述你对中断，异常，系统调用的理解

![image-20241221130223877](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221130223877.png)

# 三.进程管理

## 1.并行性与并发性的区别与联系

![image-20241221130630950](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221130630950.png)

## 5.进程状态，并说明状态转换的过程和原因

原因

![image-20241221132800408](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221132800408.png)

![image-20241221132936612](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221132936612.png)

## **6. 什么是原语？进程控制原语都有哪些，并简要说明。** 

### **总结：四种原语的作用与关系**

| **原语类型** | **作用**                                   | **使用场景**                     |
| :----------: | ------------------------------------------ | -------------------------------- |
|   创建原语   | 创建新进程，并分配资源                     | 新任务启动时                     |
|   撤销原语   | 终止进程，释放其占用的资源                 | 任务完成或需要强制终止时         |
|   阻塞原语   | 将进程转为阻塞状态，等待事件或资源         | 资源不足或事件未到达时           |
|   唤醒原语   | 将阻塞进程转为就绪状态，使其可以被调度运行 | 阻塞原因消除，资源或事件准备好时 |

**7. 什么是进程间的互斥?什么是进程间同步?使用 P，V 操作举例说明互斥和同步的实现。【注：P 即 wait,V 即 signal】**

![image-20241221133729468](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221133729468.png)

## 生产者消费者

P（mutex）只是加锁的过程，具体的操作你需要自己写，加锁之前你得判断一下是否还有空闲的缓冲区。

![image-20241221164022972](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221164022972.png)

## 车间装配

![image-20241221185143144](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221185143144.png)

```
A车间
while(1){
	生产一个产品A;
	P(empty1);
	P(mutex1);
	把产品A放到F1的货架上;
	V(mutex1);
	V(full1);
}

B车间
A车间
while(1){
	生产一个产品B;
	P(empty2);
	P(mutex2);
	把产品B放到F2的货架上;
	V(mutex2);
	V(full2);
}
装配车间
while(1){
	P(full1);
	P(mutex1);
	从F1上拿去一个A零件；
	V(mute1);
	V(full1);
	
    P(full2);                   // 等待 F2 上有零件 B
    P(mutex2);                  // 加锁，互斥访问货架 F2
    从货架 F2 上取一个零件 B；       // 取出零件 B
    V(mutex2);                  // 解锁，释放对 F2 的访问
    V(empty2);                  // 通知车间 B F2 空出一个位置
    
    将A和B装配成一个零件
}
```

## 什么是线程，和进程的区别？


​	线程是进程内调度和分配 CPU 的基本单位，线程共享进程的资源（如地址空间、文件等），而进程是资源分配的基本单位，拥有独立的资源。

**区别：**

1. **资源**：线程共享资源，进程拥有独立资源。
2. **切换**：线程切换效率高，进程切换开销大。
3. **通信**：线程间通信简单，进程间通信复杂。
4. **调度**：线程调度可由用户或内核控制，进程调度由内核完成。
5. **状态**：线程无挂起状态，进程有挂起状态。





## 控制系统中的数据采集

![image-20241221191641091](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221191641091.png)

## 原子操作与临界区的区别：

1. 定义
   - 原子操作：不可分割的操作，由硬件或自旋锁实现。
   - 临界区：访问共享资源的一段代码，不允许并发访问。
2. 粒度
   - 原子操作粒度小（单变量操作）。
   - 临界区粒度大（多步或复杂操作）。
3. 实现
   - 原子操作通过硬件指令实现。
   - 临界区通过访问标志、互斥量等机制实现。
4. 场景
   - 原子操作适合简单的变量操作。
   - 临界区适合保护复杂的共享资源访问。

## 使用fork和pipe创建子进程和通道

`lockf(fd, 1, 0)`：加写锁，确保管道的写端操作是互斥的。

`lockf(fd, 0, 0)`：释放写锁，允许其他进程对管道写端进行操作。

使用 `lockf` 可以保证多个进程对共享资源（如文件或管道）的顺序访问，避免数据竞争或冲突。

![image-20241221193536475](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221193536475.png)

```c
main() {
    int r, p1, p2, p3, fd[2];          // r: 读取返回值；p1, p2, p3: 子进程的 PID；fd[2]: 管道文件描述符
    char buf[50], s[50];               // buf: 用于写入的数据；s: 用于从管道读取的数据

    pipe(fd);                          // 创建管道，fd[0] 为管道读端，fd[1] 为管道写端

    while ((p1 = fork()) == -1);       // 创建子进程 P1，如果 fork 失败，持续重试

    if (p1 == 0) {                     // 子进程 P1 执行的代码
        lockf(fd[1], 1, 0);            // 对管道的写端加锁，确保互斥写入
        sprintf(buf, "Child process P1 is sending message!\n"); // 将要发送的消息存入 buf
        printf("Child process P1!\n"); // 打印子进程 P1 的标识信息
        write(fd[1], buf, 50);         // 将 buf 中的数据写入管道
        sleep(5);                      // 模拟写入后的延迟，确保父进程有时间读取数据
        lockf(fd[1], 0, 0);            // 解锁管道的写端，允许其他进程写入
        exit(0);                       // 子进程 P1 退出
    } else {
        while ((p2 = fork()) == -1);   // 创建子进程 P2，如果 fork 失败，持续重试

        if (p2 == 0) {                 // 子进程 P2 执行的代码
            lockf(fd[1], 1, 0);        // 对管道的写端加锁，确保互斥写入
            sprintf(buf, "Child process P2 is sending message!\n"); // 将要发送的消息存入 buf
            printf("Child process P2!\n"); // 打印子进程 P2 的标识信息
            write(fd[1], buf, 50);     // 将 buf 中的数据写入管道
            sleep(5);                  // 模拟写入后的延迟，确保父进程有时间读取数据
            lockf(fd[1], 0, 0);        // 解锁管道的写端，允许其他进程写入
            exit(0);                   // 子进程 P2 退出
        } else {
            while ((p3 = fork()) == -1); // 创建子进程 P3，如果 fork 失败，持续重试

            if (p3 == 0) {             // 子进程 P3 执行的代码
                lockf(fd[1], 1, 0);    // 对管道的写端加锁，确保互斥写入
                sprintf(buf, "Child process P3 is sending message!\n"); // 将要发送的消息存入 buf
                printf("Child process P3!\n"); // 打印子进程 P3 的标识信息
                write(fd[1], buf, 50); // 将 buf 中的数据写入管道
                sleep(5);              // 模拟写入后的延迟，确保父进程有时间读取数据
                lockf(fd[1], 0, 0);    // 解锁管道的写端，允许其他进程写入
                exit(0);               // 子进程 P3 退出
            }
        }
    }

    wait(0);                           // 父进程等待子进程 P1 执行完毕
    if ((r = read(fd[0], s, 50)) == -1) { // 父进程从管道读端读取数据
        printf("Can't read pipe\n");   // 如果读取失败，打印错误信息
    } else {
        printf("%s\n", s);             // 读取成功，打印子进程 P1 的消息
    }

    wait(0);                           // 父进程等待子进程 P2 执行完毕
    if ((r = read(fd[0], s, 50)) == -1) { // 父进程从管道读端读取数据
        printf("Can't read pipe\n");   // 如果读取失败，打印错误信息
    } else {
        printf("%s\n", s);             // 读取成功，打印子进程 P2 的消息
    }

    wait(0);                           // 父进程等待子进程 P3 执行完毕
    if ((r = read(fd[0], s, 50)) == -1) { // 父进程从管道读端读取数据
        printf("Can't read pipe\n");   // 如果读取失败，打印错误信息
    } else {
        printf("%s\n", s);             // 读取成功，打印子进程 P3 的消息
    }

    exit(0);                           // 父进程结束
}

```

## 请给出 PCB 的主要内容。描述当进程发生下述转移时:就绪>运行、运行>阻塞，操作系统需要使用/修改 PCB 的那些内容?

![image-20241221194333971](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221194333971.png)

# 处理机调度

## 1. 什么是分级调度?分时系统中有作业调度的概念吗?如果没有，为 什么?

![image-20241221200609092](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221200609092.png)

![image-20241221200628594](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221200628594.png)

![image-20241221200614593](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221200614593.png)

## 分级调度

![image-20241221222917819](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221222917819.png)

还有一个需要注意的是，就是如果在调用其他优先级的进程的时候如果优先级更高的进程出现了就绪状态，优先处理高优先级的进程

![image-20241221222908468](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221222908468.png)

## 计算周转周期

![image-20241221223048924](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241221223048924.png)

利用率的时间是总的时间

## 计算机周期

- 下面这题很简单，把各种不同的调度方式记住就好了

SPF和SLF一样，叫法不同



非剥夺是优先级调度不会因为别的优先级高而被抢占

![image-20241222151202778](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222151202778.png)

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222151139647.png)

![image-20241222151247991](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222151247991.png)

![image-20241222151318390](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222151318390.png)

## 什么是死锁？死锁的原因和必要条件，怎么预防

![image-20241222151632277](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222151632277.png)

![image-20241222151640375](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222151640375.png)

## 银行家算法

### Need矩阵

![image-20241222154404631](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222154404631.png)

### 安全序列

![image-20241222154430194](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222154430194.png)

## 周转时间，带权周转时间

![image-20241222160206127](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222160206127.png)

# 内存管理

## 动态分配算法，很简单

![image-20241222163020316](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222163020316.png)

![image-20241222163033092](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222163033092.png)

## 页式管理

- 缺页中断：已知的页号不存在于页号之中，没有对应的块号（但是又没有超出长度）
- 越界中断：就是直接超过了规定的页号长度

主要记住公式：第几页等于总的内存空间/一页的大小，剩下的就是页内的偏移

![image-20241222164155813](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222164155813.png)

## 二级页表管理方式

![image-20241222165437020](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222165437020.png)

![image-20241222165431164](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222165431164.png)

## 淘汰算法计算缺页率

![image-20241222170549565](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222170549565.png)

- 替换的规则

![image-20241222170811260](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222170811260.png)

- 简单clock 扫描到第一个r = 0
- **改进型clock 扫描导第一个r=0且m = 0**

![image-20241222201910965](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222201910965.png)

## 地址转换

![image-20241222202702346](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222202702346.png)

![image-20241222202940077](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222202940077.png)

# 设备管理

## 磁道计算

![image-20241222213850904](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241222213850904.png)