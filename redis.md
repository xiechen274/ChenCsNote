# 整合SpringBoot

## 单机整合

### 序列化问题

- 在传入参数的过程中会出现编码错误（由于使用了jdk默认的序列化机制），需要将对象进行序列化

**第一种解决方案**

1.使用StringRedisTemplate

![image-20241006160157986](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241006160157986.png)

![image-20241006160102598](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241006160102598.png)

**第二种解决方案**

#### 配置文件解决序列化问题

使用Redis配置文件，指定Redis序列化的方式

```java
package com.atguigu.redis7.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.data.redis.connection.lettuce.LettuceConnectionFactory;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.data.redis.serializer.GenericJackson2JsonRedisSerializer;
import org.springframework.data.redis.serializer.StringRedisSerializer;
import org.springframework.stereotype.Component;

/**
 * @auther zzyy
 * @create 2022-12-14 20:50
 */
@Configuration
public class RedisConfig
{
    /**
     * redis序列化的工具配置类，下面这个请一定开启配置
     * 127.0.0.1:6379> keys *
     * 1) "ord:102"  序列化过
     * 2) "\xac\xed\x00\x05t\x00\aord:102"   野生，没有序列化过
     * this.redisTemplate.opsForValue(); //提供了操作string类型的所有方法
     * this.redisTemplate.opsForList(); // 提供了操作list类型的所有方法
     * this.redisTemplate.opsForSet(); //提供了操作set的所有方法
     * this.redisTemplate.opsForHash(); //提供了操作hash表的所有方法
     * this.redisTemplate.opsForZSet(); //提供了操作zset的所有方法
     * @param lettuceConnectionFactory
     * @return
     */
    @Bean
    public RedisTemplate<String, Object> redisTemplate(LettuceConnectionFactory lettuceConnectionFactory)
    {
        RedisTemplate<String,Object> redisTemplate = new RedisTemplate<>();

        redisTemplate.setConnectionFactory(lettuceConnectionFactory);
        //设置key序列化方式string
        redisTemplate.setKeySerializer(new StringRedisSerializer());
        //设置value的序列化方式json，使用GenericJackson2JsonRedisSerializer替换默认序列化
        redisTemplate.setValueSerializer(new GenericJackson2JsonRedisSerializer());

        redisTemplate.setHashKeySerializer(new StringRedisSerializer());
        redisTemplate.setHashValueSerializer(new GenericJackson2JsonRedisSerializer());

        redisTemplate.afterPropertiesSet();

        return redisTemplate;
    }
}
```

### 简单代码

```java
package com.atguigu.redis7.service;

import cn.hutool.db.sql.Order;
import com.sun.org.apache.xpath.internal.operations.Or;
import io.netty.util.SuppressForbidden;
import lombok.extern.slf4j.Slf4j;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.data.redis.core.StringRedisTemplate;
import org.springframework.stereotype.Service;

import javax.annotation.Resource;
import java.util.UUID;
import java.util.concurrent.ThreadLocalRandom;

/**
 * @auther zzyy
 * @create 2022-12-14 20:51
 */
@Service
@Slf4j
public class OrderService
{

    public static final String ORDER_KEY = "ord:";

    @Resource private RedisTemplate redisTemplate;
    //@Resource private StringRedisTemplate StringRedisTemplate;

    public void addOrder(){
        int keyId = ThreadLocalRandom.current().nextInt(1000)+1;
        String orderNo = UUID.randomUUID().toString();
        redisTemplate.opsForValue().set(ORDER_KEY+keyId,"京东订单"+orderNo);
        log.info("成功创建流水编号为" + keyId + "的订单编号");
    }


    public String getOrderById(Integer keyId)
    {
        return  (String) redisTemplate.opsForValue().get(ORDER_KEY+keyId);
    }

}
```

## 集群整合

这个需要三台虚拟机。。。就不整合了

### 集群配置文件参考

```java
# ========================redis集群=====================
spring.redis.password=111111
# 获取失败 最大重定向次数
spring.redis.cluster.max-redirects=3
spring.redis.lettuce.pool.max-active=8
spring.redis.lettuce.pool.max-wait=-1ms
spring.redis.lettuce.pool.max-idle=8
spring.redis.lettuce.pool.min-idle=0
spring.redis.cluster.nodes=192.168.111.175:6381,192.168.111.175:6382,192.168.111.172:6383,192.168.111.172:6384,192.168.111.174:6385,192.168.111.174:6386
```

#### SpringBoot中的redis集群高可用

- 模拟主机宕机

**测试的结果是：java微服务没有发现Redis集群新的拓扑结构**，没有动态刷新新的拓扑结构

![image-20241006164518824](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241006164518824.png)

问题原因

![image-20241006164656421](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241006164656421.png)

#### 解决拓扑动刷新

![image-20241006164753878](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20241006164753878.png)

在配置文件中设置拓扑文件的刷新时间，保障高可用

```java
spring.redis.lettuce.cluster.refresh.adaptive=true
spring.redis.lettuce.cluster.refresh.period=2000
spring.redis.cluster.nodes=192.168.111.185:6381,192.168.111.185:6382,192.168.111.172:6383,192.168.111.172:6384,192.168.111.184:6385,192.168.111.184:6386
```

