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