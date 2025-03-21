# 1.计算机网络和因特网![扫描全能王 2023-11-20 20.13_1](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_1.jpg)

![扫描全能王 2023-11-20 20.13_2](/Users/xiechen/Downloads/CamScanner231120202056076/扫描全能王 2023-11-20 20.13_2.jpg)



![扫描全能王 2023-11-20 20.13_2](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_3.jpg)



![扫描全能王 2023-11-20 20.13_4](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_4.jpg)

![扫描全能王 2023-11-20 20.13_5](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_6.jpg)

![扫描全能王 2023-11-20 20.13_7](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_7.jpg)

![扫描全能王 2023-11-20 20.13_8](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_8.jpg)

![扫描全能王 2023-11-20 20.13_9](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_9.jpg)

![扫描全能王 2023-11-20 20.13_10](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_10.jpg)

![扫描全能王 2023-11-20 20.13_11](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_12.jpg)

![扫描全能王 2023-11-20 20.13_15](/Users/xiechen/Downloads/CamScanner231120202056076/扫描全能王 2023-11-20 20.13_15.jpg)

![扫描全能王 2023-11-20 20.13_14](/Users/xiechen/Downloads/CamScanner231120202056076/扫描全能王 2023-11-20 20.13_14.jpg)

![扫描全能王 2023-11-20 20.13_13](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E6%89%AB%E6%8F%8F%E5%85%A8%E8%83%BD%E7%8E%8B%202023-11-20%2020.13_13.jpg)

# 2.应用层![长图 2023-11-20 20.31.10](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/%E9%95%BF%E5%9B%BE%202023-11-20%2020.31.10.jpg)

## 2.7套接字编程

![image-20231120203824652](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120203824652.png)

应用进程之间若要远程的传输报文，需要借用传输层来实现，二者之间通过socket连接，进行收，发送，进程结束之后再关闭socket

**应用进程不需要关心怎么建立连接**，由socket api来建立

![image-20231120204335003](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120204335003.png)

### TCP socket编程

![image-20231120204519458](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120204519458.png)

连接的过程

cs模式中，服务器先运行，服务器创建欢迎socket

之后客户端创建本地socket，与本地端口隐式捆绑，与服务器请求连接

![image-20231120204625255](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120204625255.png)

**sockaddr_in数据结构**

ip与port的捆绑

![image-20231120205830350](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120205830350.png)

![image-20231120205901419](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120205901419.png)

**host_ent数据结构**

主要是域名解析的调用

![image-20231120205953017](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120205953017.png)

![image-20231120210030479](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120210030479.png)

交互过程

都是socket和本地port建立捆绑，然后才能调用connect

![image-20231120211628709](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120211628709.png)

![image-20231120211852159](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120211852159.png)

![image-20231120212417529](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231120212417529.png)

### 看书总结



# 传输层



![image-20231204112438526](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204112438526.png)

多路复用

![image-20231204112559946](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204112559946.png)

通过源端ip目标ip

***源端口，目标端口进行解复用，多路复用*** ----------存放在TCP或者UDP的表头当中 ，复用的过程主要是把协议的数据部分交给服务器或者应用进程

![image-20231204115315352](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204115315352.png)

UDP中之和本地的id和端口进行捆绑，和远端没关系

# 网络层

## 4.1导论

![image-20240402104823440](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402104823440.png)

​	转发和路由 网络层的主要功能

过程

![image-20240402104950250](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402104950250.png)

每一跳都要进行解封装，寻找下一个路由地址（选择路径），封装解封装

路由是控制层面，转发是数据平面的功能

![image-20240402105400236](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402105400236.png)

![image-20240402105410655](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402105410655.png)

传统方式的转发，耦合度高，可维护性低，且为分布式处理

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402110310715.png)

网络层的链接与传输层的链接不相同，传输层是对端到端的链接，通过网络层为媒体的这种叫做面向连接，相当于tcp的就是面向连接，而网络层的连接就是实打实的连接，路由器的算法实现了控制平面的功能

![image-20240402111056222](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402111056222.png)

网络提供的服务指标（服务模型）

![image-20240402111110538](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402111110538.png)

## 4.2路由器的组成

![image-20240402111446086](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402111446086.png)

fabric通过输入端空与输出端口进行转发，

输入端口的功能，转换信号，封装解封装![image-20240402112320256](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402112320256.png)

![image-20240402112058852](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402112058852.png)

路由的输入端口前也有queue的缓存（输出的端口也有）

fabric的交换机构

![image-20240402112500275](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402112500275.png)

bus是计算机总线，将数据封装成帧通过总线来控制输出的网卡

通过内存需要通过两次 system bus，时间较慢![image-20240402112621982](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402112621982.png)

通过总线交换，只需要通过一次bus

![image-20240402112733410](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402112733410.png)

![image-20240402112902727](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402112902727.png)

封装成帧之后，分组并不是先到先出，而是还会经过一些选择算法，选出可以优先打出的分组，通过cpu来调度优先进程，不是简单的输出队列

![image-20240402113355329](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402113355329.png)

输出端口的排队

![image-20240402113419680](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402113419680.png)

 输出的调度机制

- 先来先服务

- 通过优先权来调度

- 

  

  ![image-20240402113738828](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402113738828.png)

  

![image-20240402113458324](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240402113458324.png)