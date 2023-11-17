# 2.拜访对象村

1.Java程序是由一组类所组成，其中一个类必须带有启动用的main方法



## 要点

面向对象设计扩展功能不需要改动之前已经测试好的程序代码

所有的JAVA程序都定义在类中

类如同蓝图描述该类型的对象要如何创建

对象自治；你无须在意她如何完成任务

对象有已知的食物，并能执行工作

对象本身已知到的事物称谓实例变量，他代表对象的状态

对象可执行的动作成为方法，他代表对象的行为

创建类时，可能同时会需要创建独立，测试用的类

类可以继承自较为抽象的父类

Java的程序在执行期是一组会相互交谈的对象

# 3.认识变量

primitive主数据类型

​	类型  	位数	值域

Boolean char

boolean 	java虚拟机决定	true或false

char 		16 bits(与c语言不同)				0~65535

数值

inerger

byte 	8bits	-128~127

short 	16bits	-32768-32767

int 	32 bits		

long 64bits

## 引用型变量

Q：我可以对引用变量进行运算吗，就像c语言那样

A：Java不是C

# 4.对象的行为，方法操作实例变量



# 5.dot com

## 加强版for循环

**for(String name:nameArray){}**

//创建名称为name的String变量，将nameArray的第一个元素赋给name，执行重复内容，止到所有的元素都被运行为止

# 6.认识api

## Arraylist（超级好用的一个类，跟链表好像）

*主要常用方法*

```java
add(Object elem)//向list中加入对象参数
remove(int index)//在索引中移除对象
renive(Object elem)//移除该对象
contains(Object elem)//如果对象与参数匹配则返回true
isEmpty()//如果List中没有元素就返回true
indexOf(Object elem)//返回对象的索引或-1
size()//返回list中的元素个数
get(int index)//返回当前索引的对象
```





![IMG_6309](C:\Users\谢隆杰\Desktop\IMG_6309.jpeg)



## 函数库（API）

放置一个import再程序源文件最前面

或者![image-20230623210906110](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623210906110.png)

![image-20230623210915964](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623210915964.png)

![image-20230623211016757](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623211016757.png)



**除了lang包之外都需要指定全名**

**传统数组可以用length这个变量取得大小**

# 继承与多态

![image-20230623211322717](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623211322717.png)

子类继承要有***extends***这个关键词

寻找两者之前的抽象关系is-a判断，什么什么是什么

![image-20230623211617028](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623211617028.png)

还需要注意super这个关键词![image-20230623211645171](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623211645171.png)

**继承让你可以确保某个父型之下的所有类都会有父型所持有的全部方法（可以继承的）**



继承所有遵守的合约:覆盖的规则

- 参数必须要一样，返回值必须要兼容![image-20230623211946244](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623211946244.png)

  

- 不能降低方法的存取权限

  

  

**方法的重载**

1. 返回类型可以不同

2. 不能只改变返回类型

3. 可以更改存取权限

   

# 接口与抽象类

![image-20230623212329676](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623212329676.png)

​									***抽象类的定义***

![image-20230623212951996](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623212951996.png)

![image-20230623213002506](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623213002506.png)

super**调用父类方法示例**

![image-20230623213033072](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623213033072.png)

![image-20230623213041094](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623213041094.png)

接口的产生用于新的类无法对其他的类通过is—a测试时就涉及不继承其他的类

机器狗—狗-动物

![image-20230623213204896](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230623213204896.png)

## 构造器与垃圾收集器



# 10.数字与静态

### **final**关键字

![image-20230712100234952](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712100234952.png)

​																	*感觉有点类似c的const*

#### 静态final的初始化



![image-20230712100541239](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712100541239.png)

final不能被覆盖或者创建子类，也不能够继承

![image-20230712101009490](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712101009490.png)

## Math的方法

**1.random()**

返回介于0.0~1，0之间的双精度浮点数

double r1=Math.random();

**2.abs()**

与c语言不同的是这个abs会自动区分浮点型数据还是整形数据来调整返回值

**3.round()**

四舍五入

**4.min()**

返回两参数中较小的一个，同样也有不通传入参数的重载

**5.max**

同上，返回较大。

## autoboxing

5.0之后的版本加入的autoboxing这个功能能够自动的将primitive主数据类型转换成包装过的对象，如可以直接使用主数据类型添加对象倒arraylist中

## 包装的静态实用性方法

**Integer**

![image-20230712102859717](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712102859717.png)

其中boollean表达值用的是自己的方法

### 数字的格式化.String.format()

*将primitive主数据类型转换为String类型*



![image-20230712103318703](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712103318703.png)

其中"%,d"控制了数字以有逗号的形式表示

**格式化的格式**

![image-20230712103924791](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712103924791.png)

**日期的格式化**

![image-20230712104547445](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712104547445.png)

最后的这个"<"挺有意思，代表重复使用today这个参数

**如果不仅仅是要对今天的日期进行操作，就需要用到其他的类*

**Calendar**（可以做涉及到日期的加减或者位移）

Calendar是一个抽象类，他的下方继承了很多个子类，原因是考虑到全球的日历标准，可以根据不同的日历来活得不同的子类。

**涉及到了获得抽象类子类的实例**

![image-20230712110732637](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712110732637.png)

![image-20230712111118547](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712111118547.png)

![image-20230712111145494](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230712111145494.png)精华部分



# 异常处理

![image-20230717234130767](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230717234130767.png)

# 12.图形用户接口

## 简单gui创建

```java
import javax.swing.*;

public class demo1 {
    public static void main(String[] args) {
        JFrame myframe =new JFrame();//创建框架
        JButton button = new JButton("click me");//添加button组件
        myframe.getContentPane().add(button);
        myframe.setSize(300,300);
        myframe.setVisible(true);
    }
}
```



存在于javax.swing这个包中，包含了很多gui组件

![image-20230718103144941](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230718103144941.png)

设置完按钮等组件，就要开始为按钮赋予功能

![image-20230718103806084](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230718103806084.png)

捕捉用户click的这个动作，执行动作对应的方法

**内部类**

![image-20230718110312008](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230718110312008.png)

![image-20230718110340498](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230718110340498.png)

*内部类可以使用外部类的方法与变量，就算是私有的也一样*，这里的外部类是对于内部类所属的外部类![image-20230718110651185](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718110651185.png)



