# Java

## 1.ideal的使用

![image-20230512202424735](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230512202424735.png)

path环境变量配，可以用于命令行窗口打开应用程序

![image-20230512204201290](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230512204201290.png)

![image-20230512204729125](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230512204729125.png)

### 快捷键

选中需要的代码，ctrl+alt+t可以自动把代码放入一个死循环的while语句

![image-20230512205500647](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230512205500647.png)

![image-20230608110937574](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230608110937574.png)快捷遍历





![image-20230512210206189](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230512210206189.png)

alt+回车在对应的方法名可以自动创建一个方法

右键之后rename

删除文件的时候如果直接再idea deleate文件再创建相同工程名的工程时，会显示已经有过改工程，即使这个工程已经被删掉，所以建议直接在磁盘里面解决
	

### 如何打开工程

files->open	关闭工程可以直接关闭ide或者直接在file里面<u>close</u>

**debug**

![image-20230515165738430](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230515165738430.png)



## 2.数据类型

### 1.注释

与 c语言一样

![image-20230513195630966](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513195630966.png)

*注释之所以不会影响程序的执行是因为最后编译的class文件里面不会包含注释*

![image-20230513195902382](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513195902382.png)

### 2.字面量（书写格式）

​		输出数字的话不用双引号（跟c语言不太一样，不需要双引号加占位符）

​		`println后面的“ln"包含了换行`

​		字符串与c语言一样双引号

​		单个字符单引号

### 3.变量

数据类型 变量名称 = 初始值；

double	money = 3.0;

```
System.out.println(money);
//输出结果为3.0
```



```
System.out.println("money");
//输出结果为money
```

### 4.变量的使用注意事项

1.变量需要先声明再使用

2.声明完就无法在存储其他数据类型的数据

### 5.变量在计算机中的底层原理

#### 1.存储形式

字符存储，以ascii的二进制形式存储

A=65, a=97, 0 =48

图片视频等数据也是二进制存储

#### 2.进制转换

##### 十进制转二进制

除二取余法

![image-20230513202629578](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513202629578.png)

##### 八进制，十六进制

![image-20230513203143375](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513203143375.png)

```
System.out.println("money");
        int a=0141;
        System.out.println(a);
        int b=0xA;
        System.out.println(b);
        //再赋值的时候在前面加上0 表示八进制0x是十六进制
        
```

运行结果![image-20230513203502940](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513203502940.png)

##### 数据大小

![image-20230513203727423](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513203727423.png)

### 6.数据类型

![image-20230513204057800](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513204057800.png)

#### 布尔值

取值范围只有true,false

#### long

定义long类型的变量，需要在数据最后加上L或者l

```java
long lg=12345678920l;
```

byte short char是直接转换为int类型参与运算的

#### char

汉字也是字符型变量

char = '中'；

#### 字符串类型(引用数据类型)

```java
String ch="西门吹雪";
        System.out.println(ch);

```

### 7.关键词，标识符

表舒服，只能由数字下划线和美元符号(c语言也可以用美元)组成

不能以数字开头，不能是关键词

### 8.数据类型的补充

`https://www.runoob.com/java/java-basic-datatypes.html`

#### final

用于修饰常变量，变量用大写英文命名

```java
 public class finalMod {

     public static void main(String[] args) {
         final double PI=3.14;
         System.out.println(PI);
     }
}

```

运行结果

![image-20231007190152867](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231007190152867.png)



#### 关于long的数据定义

**Java 里使用 long 类型的数据类型若他的值大于int的最大存储极限要在数值后面加上 L，否则将作为整型解析：**



```java
long g = (long)9223372036854775807;
long h = (long)-9223372036854775808;

或者

long g = 9223372036854775807;
long h = -9223372036854775808;
```

会出现以下报错信息：

```java
Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
The literal 9223372036854775807 of type int is out of range
The literal 9223372036854775808 of type int is out of range 
```

溢出了~

解决方法在数值后面加上 **L**：

```java
long value = 9223372036854775807L;
```



#### 关于小于int数据类型的强制转换

```
short a = 1;
short b = 2;
```

**那么 a+b 是什么类型？**

答：在java的世界里，如果比int类型小的类型做运算，java在编译的时候就会将它们统一强转成int类型。当是比int类型大的类型做运算，就会自动转换成它们中最大类型那个。



#### 关于成员变量，局部变量，静态变量的代码表述

```java
public class RunoobTest {
    // 成员变量
    private int instanceVar;
    // 静态变量
    private static int staticVar;
    
    public void method(int paramVar) {
        // 局部变量
        int localVar = 10;
        
        // 使用变量
        instanceVar = localVar;
        staticVar = paramVar;
        
        System.out.println("成员变量: " + instanceVar);
        System.out.println("静态变量: " + staticVar);
        System.out.println("参数变量: " + paramVar);
        System.out.println("局部变量: " + localVar);
    }
    
    public static void main(String[] args) {
        RunoobTest v = new RunoobTest();
        v.method(20);
    }
}
```

#### 关于实例变量访问范围的补充

java 实例变量在整个类内部是可访问的，而不管实例变量声明在类的哪个位置。

```java
import java.io.*;

public class Employee{

    public Employee (String empName){
        name = empName;
    }
    
    public void setSalary(double empSal){
        salary = empSal;
    }
    
    public void printEmp(){
        System.out.println("name:" + name);
        System.out.println("salary:" + salary);
    }
    
    public static void main(String args[]){
        Employee empOne = new Employee("RUNOOB");
        empOne.setSalary(1000);
        empOne.printEmp();
        System.out.println(empOne.salary);
    }
    public String name;
    private double salary;
}
```

比如在上面代码中，***尽管实例变量声明在类的尾部***，在之前方法中仍可访问。

## 3.运算符，表达式和语句

### 输入与输出

```Java
Scanner scanner = new Scanner(System.in);//创建一个scanner对象

System.out.print("Enter your age: ");
int age = scanner.nextInt();
scanner.nextLine();  // 读取剩余的换行符

System.out.print("Enter your name: ");
String name = scanner.nextLine();

System.out.println("Your name is " + name + " and your age is " + age);
```

*与c语言sacnf和getchar类似，在读取字符串或者字符的时候需要用nextLine()读取缓冲区的换行符*

#### 补充

##### 1. **next() 与 nextLine() 区别**

next():

- 1、一定要读取到有效字符后才可以结束输入。
- 2、对输入有效字符之前遇到的空白，next() 方法会自动将其去掉。
- 3、只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符。
- next() 不能得到带有空格的字符串。

nextLine()：

- 1、以Enter为结束符,也就是说 nextLine()方法返回的是输入回车之前的所有字符。
- 2、可以获得空白。



##### 2.Console

输入的时候字符都是可见的，所以Scanner类不适合从控制台读取密码。从Java SE 6开始特别引入了Console类来实现这个目的。若要读取一个密码，可以采用下面这段代码：

```java
Console cons = System.console();
String username = cons.readline("User name: ");
char[] passwd = cons.readPassword("Password: ");
```

为了安全起见，返回的密码存放在一维字符数组中，而不是字符串中。在对密码进行处理之后，应该马上用一个填充值覆盖数组元素。

采用Console对象处理输入不如采用Scanner方便。每次只能读取一行输入，而没有能够读取一个单词或者一个数值的方法。

### 类型转换

#### 	自动转换

小范围变量可以指及赋值给大范围变量

![image-20230514025330881](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514025330881.png)



#### 在表达式中的转换

表达式中的最终结果又表达式中的最高类型决定

#### 强制转换

![image-20230514030712671](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514030712671.png)

强制转换的底层原理，可能存在精度丢失![image-20230514030846260](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514030846260.png)

### 运算符（主要列出与c语言不同的地方）

https://www.runoob.com/java/java-operators.html

#### "+"

***在做字符算运算的时候加号的作用是将两个字符串连接在一起*与c语言有很大不同**

![image-20230514031828597](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514031828597.png)

```Java
System.out.println("abc"+"c");
        System.out.println("abc"+5);
        int a=5,b=3;
        System.out.println(a+b);
        System.out.println("a"+5+"ji");
        //能算则算，不能算连接
```

![image-20230514032220018](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514032220018.png)

运行结果

#### 关系运算符

与c语言不同的是这边关系运算符的返回值是布尔值，true或者false,

![image-20230514110455849](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514110455849.png)

运算结果

```
true
false
```

#### 逻辑运算符

![image-20230514111150261](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514111150261.png)

单目与双目逻辑符的区别，

```
a=100;                                           
b=10;                                            
System.out.println(a>b||++b<10);                 
System.out.println(b);    //检测双目运算符的短路特点        
System.out.println(a>b|++b<10);                  
System.out.println(b); //会执行++b这个操作                          
```

输出结果

![image-20230514111858864](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514111858864.png)

**按位或，按位与，按位异或，按位非这些运算符用的不多，与c语言类似，自己看就好**

#### 三元运算符

![image-20230514112010242](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514112010242.png)



```
a=100;
b=10;
System.out.println(a>b?a:b );
```

![image-20230514112436116](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514112436116.png)

了解就好，之后尽量用if语句

#### 运算符的优先级

记住一些比较特别的就好

1.双与的优先级大于双或(但是尽量还是不要用这个太多逻辑)

#### 键盘录入



![image-20230514183531769](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514183531769.png)





#### 补充

![image-20231010114025498](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231010114025498.png)

![image-20231010114346060](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231010114346060.png)

这个太细节了



![image-20231010114017870](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231010114017870.png)

![image-20231010113903183](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231010113903183.png)





### 语句概述

#### 补充

for-each 循环（也称为增强 for 循环）和普通的 for 循环在用法和行为上有一些重要的不同：

**for-each 循环**：

1. **用于遍历集合和数组**：for-each 循环主要用于遍历集合（如 ArrayList、HashSet）和数组，不适用于其他数据结构。

2. **简化的语法**：for-each 循环提供了一种更简洁的语法，不需要显式地管理索引或迭代器。它自动迭代集合中的每个元素。

3. **只读**：在 for-each 循环中，你只能访问集合或数组的元素，而不能修改它们的值。这是一种只读操作，不适用于修改元素。

示例：

```java
List<String> list = new ArrayList<>();
for (String item : list) {
    System.out.println(item); // 遍历并输出元素
}
```

**普通的 for 循环**：

1. **通用性**：普通的 for 循环可以用于遍历集合和数组，也可以用于其他情况，如控制循环次数、遍历范围、以及条件循环等。

2. **需要显式索引**：普通的 for 循环需要你显式地使用索引变量来控制循环，你可以使用索引来访问和修改数组或集合的元素。

3. **可读写**：你可以使用普通的 for 循环来修改数组或集合的元素。

示例：

```java
int[] arr = new int[5];
for (int i = 0; i < arr.length; i++) {
    arr[i] = i; // 初始化数组元素
}
```

总之，for-each 循循环适用于简单的遍历操作，而普通的 for 循环更加通用，适用于各种不同的循环场景，包括遍历和修改元素。你可以根据具体的需求来选择使用哪种循环结构。

```java
package temp;

import java.util.Arrays;

public class temp6 {
    public static void main(String[] args) {
        int[] str = new int[10];
        for(int i : str){
            str[i]=i;//只读模式，无法修改数组的值
        }
        System.out.println(Arrays.toString(str));//所以打印出来的值还是0
    }
}


```

**需要十分注意的是！！**

for-each中 i的值是元素值，不是索引值

#### if语句

if语句的布尔表达式同样是true和false。

### switch语句

同c语言，switch语句中的表达式和枚举量只能是整型常量（byte,short，int,char)

### Random类的使用

Random 名字 = new Random()

![image-20230517104028826](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517104028826.png)

**需要注意的是随机数是0-n-1**



![*image-20230517104433436*](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517104433436.png)

***解决从n开始的随机数问题***

> **案例**
>
> *猜数字游戏*
>
> ## ![image-20230517104806894](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517104806894.png)
>
> 
>
> 



### 修饰符

`https://www.runoob.com/java/java-modifier-types.html`

修饰符用来定义类、方法或者变量，通常放在语句的最前端。

#### 访问修饰符

Java中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。Java 支持 4 种不同的访问权限。

- **default** (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法。

- **private** : 在同一类内可见。使用对象：变量、方法。 **注意：不能修饰类（外部类）**

- **public** : 对所有类可见。使用对象：类、接口、变量、方法

- **protected** : 对同一包内的类和所有子类可见。使用对象：变量、方法。 **注意：不能修饰类（外部类）**。

  接口不能用protected来修饰

我们可以通过以下表来说明访问权限：

| 修饰符      | 当前类 | 同一包内 | 子孙类(同一包) | 子孙类(不同包)                                               | 其他包 |
| :---------- | :----- | :------- | :------------- | :----------------------------------------------------------- | :----- |
| `public`    | Y      | Y        | Y              | Y                                                            | Y      |
| `protected` | Y      | Y        | Y              | Y/N（[说明](https://www.runoob.com/java/java-modifier-types.html#protected-desc)） | N      |
| `default`   | Y      | Y        | Y              | N                                                            | N      |
| `private`   | Y      | N        | N              | N                                                            | N      |

**proctected的子孙不同包情况**

- **子类与基类在同一包中**：被声明为 protected 的变量、方法和构造器能被同一个包中的任何其他类访问；
- **子类与基类不在同一包中**：那么在子类中，子类实例可以访问其从基类继承而来的 protected 方法，而不能访问基类实例的protected方法。

关于protected的补充

https://www.runoob.com/w3cnote/java-protected-keyword-detailed-explanation.html

## 4.数组

> 再ideal中，用数组名.for i可以快速得到遍历数组的for循环，十分方便
>
> 输出arr.length可以直接输出数组长度

### 1.数组的初始化

*与c语言不同的是，java*在对存储内存地址的变量城中引用型变量，而不是指针，在Java中创建引用型变量需要**声明**和**分配**两个过程

***数组是引用型变量，所以在创建数组的过程中需要声明和分配***

**声明**

数组的元素类型[] 数组名；

或者

数组的元素类型 数组名[ ]；

**与C不同的地方是，Java不允许再声明数组的方括号内指定数组元素的个数**

其中，数组的声明和分配可以连接在一起

**分配**

数组名 []=new 数组的元素类型

**引用**

```
System.out.println(arr);
```

如果直接对数组arr进行引用，输出的是arr的地址

**但是如果是char**型的数组，则是输出全部元素。



#### 静态初始化数组

> 在Java中，数组类型的声明中，中括号可以放在类型名称后面或变量名称后面，这两种语法是等效的。**在Java中，对于数组类型的变量，我们通常将中括号放在类型名称后面，而不是变量名称后面**。
>
> ![image-20230514205311715](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514205311715.png)命名格式，其中new指的是创建一个新的东西 **一般用的是简化形式**
>
> *还有一点与c语言不同的是Java中允许在数组的初始化时，用变量来指定数组个数*
>
> ```
> int size=20;
> int [ ] size = new int[20]
> ```
>
> ![image-20230514210032317](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514210032317.png)
>
> *Java中内存地址好像会在前面添加一个数据类型的大写，@之后的是十六进制的地址名*
>
> **访问数组长度**
>
> ![image-20230514210816252](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514210816252.png)
>
> *同样跟c语言不同，不用借助库函数*

> ![](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230514211022504.png)



#### 动态数组的初始化

string数组的默认初始化的值是 null

布尔类型的数组默认初始化是fals

### 2.遍历数组

#### 1.Java特性遍历

```
int a[]={1,2,3};
       for(int i:a){
            System.out.println(i);
            }
```

Java中的简洁型遍历方式，i必须是一个没有声明过的变量且必须在for语句中定义

#### 2.toString遍历

利用Arrays中的toString方法

```
import java.util.Arrays;//导入方法
public class array {
    public static void main(String[] args) {
       int a[]={1,3,3};
        System.out.println(Arrays.toString(a));

    }
}
```

**toString**方法原理是提取数组中的元素形成字符串，引用时参数是数组名。

#### 3.排序与二分法

调用Arrays

#### 1.public static void sort(double a[ ])

从小到大排序

#### 2..public static void binarySearch(double a[ ]，double number)

### 枚举（感觉用的不多）

**定义**

```
enum 枚举名{
常量列表
}
```



```
enum season{
spring,winter,summer}//声明枚举体，枚举常量
season x;
x=season.spring//赋值枚举类型变量
```

### 补充

`https://www.runoob.com/java/java-array.html`

#### 数组声明上的问题

首先必须声明数组变量，才能在程序中使用数组。下面是声明数组变量的语法：

```java
dataType[] arrayRefVar;   // 首选的方法
 
或
 
dataType arrayRefVar[];  // 效果相同，但不是首选方法
```

建议使用 **dataType[] arrayRefVar** 的声明风格声明数组变量。 dataType arrayRefVar[] 风格是来自 C/C++ 语言 ，在Java中采用是为了让 C/C++ 程序员能够快速理解java语言。

#### 创建数组的语句步骤

java语言使用new操作符来创建数组，语法如下：

```
arrayRefVar = new dataType[arraySize];
```

上面的语法语句做了两件事：

- 一、使用 dataType[arraySize] 创建了一个数组。
- 二、**把新创建的数组的引用赋值给变量 arrayRefVar。**

数组变量的声明，和创建数组可以用一条语句完成，如下所示：

```java
dataType[] arrayRefVar = new dataType[arraySize];
```

另外，你还可以使用如下的方式创建数组。

```java
dataType[] arrayRefVar = {value0, value1, ..., valuek};
```

数组的元素是通过索引访问的。数组索引从 0 开始，所以索引值从 0 到 arrayRefVar.length-1。

#### 数组的for-Each循环

JDK 1.5 引进了一种新的循环类型，被称为 For-Each 循环或者加强型循环，它能在不使用下标的情况下遍历数组。

语法格式如下：

```java
for(type element: array)
{
    System.out.println(element);
}
```

**实例**

```java
public class TestArray {
   public static void main(String[] args) {
      double[] myList = {1.9, 2.9, 3.4, 3.5};
 
      // 打印所有数组元素
      for (double element: myList) {
         System.out.println(element);
      }
   }
}
```





#### 静态初始化和动态初始化

在Java中，数组的创建和初始化有两种方式，分别是静态初始化和动态初始化。这两种方式的语法和行为有所不同。

1. **静态初始化**：在创建数组时，可以使用静态初始化来为数组的元素分配初始值，不需要使用 `new` 关键字。

    ```java
    int[] numbers = {1, 2, 3, 4, 5};
    ```

    这种方式适用于你在创建数组的同时知道元素的初始值，并且数组的长度由初始值的个数决定。

2. **动态初始化**：如果你想在创建数组后才为元素分配初始值，可以使用动态初始化，需要使用 `new` 关键字。

    ```java
    int[] numbers = new int[5];
    ```

    这种方式适用于你事先知道数组的长度，但要在后续的代码中为元素赋值。

所以，你说的 "正常创建数组需要使用 `new`" 是指动态初始化的方式。静态初始化和动态初始化是两种不同的数组创建和初始化方式，根据具体需求选择合适的方式。如果你事先知道元素的值，可以使用静态初始化，而如果你只知道数组的长度，但不知道具体元素的值，可以使用动态初始化。



## 5.方法

### 1.方法的定义，调用

类似函数

![image-20230516141921312](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516141921312.png)



### 2.方法使用的常见问题

参考一下就好，感觉和函数差不多

![image-20230516143124805](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516143124805.png)



### 3.方法案例

### 4.方法调用的内存图

方法与方法之间可以互相调用

![image-20230516143821884](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516143821884.png)

![image-20230516144241399](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516144241399.png)

需要调用的时候再入栈，栈是先进后出



### 5.方法的参数传递机制

同样也是注意实参和形参。

![image-20230516144611365](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516144611365.png)



**引用类型的参数传递**

传递引用型变量的地址，因为引用的是地址，所以形参的改变也会是原参数的值改变，跟c语言的数组传递原理一样，数组名的本质就是地址

![image-20230516145155149](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516145155149.png)

**数组的元素存储再堆区**

​	

### 6.方法重载

**方法重载（overlode)的形式**

![image-20230516151102593](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516151102593.png)

![image-20230516151154581](D:\markdown\image-20230516151154581.png)

各种方法名字相同，但是参数和内容不同，不冲突

### return关键字

![image-20230516152138585](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230516152138585.png)

可以用于结束方法，上面的样例代码中分母的传入值如果等于零，就用return结束当前方法

## 6.面向对象

### 1.设计对象并使用

先设计类，再设计对象

![image-20230517110018870](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517110018870.png)

*如何设计类*

![image-20230517110233920](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517110233920.png)

![image-20230517110303056](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517110303056.png)

![image-20230517111003894](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517111003894.png)



**补充事项**

![image-20230517111333673](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517111333673.png)

#### 一些没听懂的个问题

> **为什么一个java文件只能有一个public类**
>
> 在Java中，一个源代码文件只能包含一个public类，这是由Java编译器的规则所决定的。这个规则是为了确保Java程序的可读性和可维护性。
>
> Java中的public类是指可以从其他源代码文件中访问的类。当一个Java源代码文件中包含一个public类时，编译器会将该类的名称作为文件名保存为.class文件，并将该.class文件放在相应的目录中。因此，Java源代码文件名必须与public类的名称相同。
>
> 如果一个Java源代码文件包含多个public类，那么编译器无法确定应该将哪个类的名称作为文件名保存为.class文件，这将导致Java程序的不可读性和不可维护性。因此，Java编译器规定一个源代码文件只能包含一个public类。
>
> 除了public类之外，Java源代码文件中还可以包含多个非public类。这些非public类是指只能从同一源代码文件中访问的类。这些非public类的名称和源代码文件名没有任何关系，因此可以在同一个源代码文件中定义多个非public类。
>
> ***成员变量前面的public修饰符可以省略吗*****
>
> 成员变量前面的public修饰符可以省略，这是因为Java中有默认访问修饰符。如果在成员变量声明时没有使用public、protected或private修饰符，则该成员变量将具有默认访问权限。
>
> 默认访问权限表示该成员变量可以在同一包内的任何类中进行访问，但是不能在不同包中的类中访问。因此，如果您的成员变量只在同一个包内的类中使用，那么可以不使用public修饰符。
>
> 需要注意的是，如果您的成员变量需要在不同包中的类中进行访问，那么必须使用public修饰符来指定该成员变量的访问权限。同样，如果您想让该成员变量只能在当前类中进行访问，那么应该使用private修饰符。如果您想让该成员变量只能在当前类和其子类中进行访问，那么应该使用protected修饰符。
>
> 



### 2.对象内存图

#### 多个对象的内存图 

![image-20230517113018211](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517113018211.png)

1.先把检索到的类放进方法去

2.把main方法放入栈区

3.对应变量加载进栈内存

4.对象的内存地址放入堆区

![image-20230517113509658](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517113509658.png)

总结

![image-20230517113647488](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230517113647488.png)





#### 两个变量指向同一个对象内存图



### 3.构造器

#### 4.this关键词	

### 5.封装

### 6.标准javabean

### 7.补充知识：成员变量，局部变量区别

### 8.面向对象综合案例

**1.案例（购物车）**

![image-20230608105516671](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230608105516671.png)

![image-20230608105649691](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230608105649691.png)



![image-20230608112226691](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230608112226691.png)

 

### 一些变量的解释

1.局部变量：在方法、构造方法、语句块中定义的变量。其声明和初始化在方法中实现，在方法结束后自动销毁

```
public class  ClassName{
    public void printNumber（）{
        int a;
    }
    // 其他代码
}
```

2.成员变量：定义在类中，方法体之外。变量在创建对象时实例化。成员变量可被类中的方法、构造方法以及特定类的语句块访问。

**成员变量相当于属性（python中）**



```
public class  ClassName{
    int a;
    public void printNumber（）{
        // 其他代码
    }
}
```

#### 成员变量与局部变量的区别

**1.声明位置不同**

成员变量也就是属性，在类中声明的。

局部变量，在方法中声明或代码块中声明。

**2.初始值不同**

成员变量如果没有赋值则是有默认值的，数据类型不同则默认值不同。

局部变量是没有默认值，也就是说必须先声明，再赋值，最后才使用。

**3.在一个类中，局部变量可以与成员变量同名，但是局部变量优先,如果非要访问成员变量的属性，则必须使用 this.color**

**this** 代表当前这个对象，也就是当前谁调用这个方法则这个对象就是谁。

#### 对象与引用区别

对象是具体的一个实例，如：**new Student();** new 表示创建一个对象，并在堆内存中开辟一块空间。

引用名称是存放的对象的地址。

3.类变量：定义在类中，方法体之外，但必须要有 static 来声明变量类型。静态成员属于整个类，可通过对象名或类名来调用。

```
public class  ClassName{
    static int a;
    public void printNumber（）{
        // 其他代码
    }
}
```

### 8.内部类的总结

https://www.runoob.com/w3cnote/java-inner-class-summary.html

内部类不是很好理解，但说白了其实也就是一个类中还包含着另外一个类。

如同一个人是由大脑、肢体、器官等身体结果组成，而内部类相当于其中的某个器官之一，例如心脏：它也有自己的属性和行为（血液、跳动）。

显然，此处不能单方面用属性或者方法表示一个心脏，而需要一个类。

而心脏又在人体当中，正如同是内部类在外部内当中。

内部类可以访问外部列的成员变量，包括私有变量

### 9.this super的用法总结

https://www.runoob.com/w3cnote/the-different-this-super.html

#### this

本质上是**指向对象本身**的一个**指针**

主要的用法

- 普通的引用，通过this来访问成员变量或者变量本身的一些属性

- 形参与成员名字重名，用this来区分

  这个的本质就是因为形参是位于方法内部，而this是该对象的指针，所以可以访问同名的成员变量而不是访问同名的形参

```java
class Person {
    private int age = 10;
    public Person(){
    System.out.println("初始化年龄："+age);
}
    public int GetAge(int age){
        this.age = age;//用this来访问私有的变量age
        return this.age;//放回从新赋值的age
    }
}
```

- 引用构造函数（与super一起介绍）

  

#### super

**super**是一个指向父类的指针，而这个超类指向的是离自己最近的一个父类

三种用法

- 也是直接引用，与this相似
- 用来引用父类中与子列相同名称的属性（成员变量或者方法）
- **引用构造函数**
  - **super(参数)**：调用父类中的某一个构造函数（应该为构造函数中的第一条语句）。
  - **this(参数)**：调用本类中另一种形式的构造函数（应该为构造函数中的第一条语句）。

运用this与super引用构造函数的时候，语句需要放在构造函数的第一条

```java
class Person { 
    public static void prt(String s) { 
       System.out.println(s); 
    } 
   
    Person() { 
       prt("父类·无参数构造方法： "+"A Person."); 
    }//构造方法(1) 
    
    Person(String name) { 
       prt("父类·含一个参数的构造方法： "+"A person's name is " + name); 
    }//构造方法(2) 
} 
    
public class Chinese extends Person { 
    Chinese() { 
       super(); // 调用父类构造方法（1） 放在第一条构造，调用没有参数的构造函数
       prt("子类·调用父类"无参数构造方法"： "+"A chinese coder."); 
    } 
    
    Chinese(String name) { 
       super(name);// 调用父类具有相同形参的构造方法（2），调用有一个name的构造函数 
       prt("子类·调用父类"含一个参数的构造方法"： "+"his name is " + name); 
    } 
    
    Chinese(String name, int age) { 
       this(name);// 调用具有相同形参的构造方法（3） 
       prt("子类：调用子类具有相同形参的构造方法：his age is " + age); 
    } 
    
    public static void main(String[] args) { 
       Chinese cn = new Chinese(); 
       cn = new Chinese("codersai"); 
       cn = new Chinese("codersai", 18); 
    } 
}
```

#### super this的异同

- super(参数)：调用基类中的某一个构造函数（应该为构造函数中的第一条语句）

- this(参数)：调用本类中另一种形成的构造函数（应该为构造函数中的第一条语句）

- super:　它引用当前对象的直接父类中的成员（用来访问直接父类中被隐藏的父类中成员数据或函数，基类与派生类中有相同成员定义时如：super.变量名 super.成员函数据名（实参） this：它代表当前对象名（在程序中易产生二义性之处，应使用 this 来指明当前对象；如果函数的形参与类中的成员数据同名，这时需用 this 来指明成员变量名）

- 调用super()必须写在子类构造方法的第一行，否则编译不通过。每个子类构造方法的第一条语句，都是隐含地调用 super()，如果父类没有这种形式的构造函数，那么在编译的时候就会报错。

- super() 和 this() 类似,区别是，super() 从子类中调用父类的构造方法，this() 在同一类内调用其它方法。

- **super() 和 this() 均需放在构造方法内第一行。**

- 尽管可以用this调用一个构造器，但却不能调用两个。

- this 和 super 不能同时出现在一个构造函数里面，因为this必然会调用其它的构造函数，其它的构造函数必然也会有 super 语句的存在，所以在同一个构造函数里面有相同的语句，就失去了语句的意义，编译器也不会通过。

- **this() 和 super() 都指的是对象，所以，均不可以在 static 环境中使用。包括：static 变量,static 方法，static 语句块**。

    `下面是对静态的补充`

  ```java
  /*
  
  想象你是一位老师，教授学生们数学课。你的学生每天都可能会有新的问题，需要你解答。但是，有些信息是对所有学生都一样的，不会随着学生的增加而改变，比如数学的常数π（pi）的值，或者学校的名称等。
  
  现在，你作为老师有一个大黑板，上面可以写一些所有学生共同需要的信息，比如π的值，或者一些通用的数学规则。这些信息是共享的，不会因为有新学生而改变，所有学生都可以看到并使用这些信息。
  
  这个大黑板上的信息就好比是静态的，因为它们是通用的，对所有学生都一样。而每个学生自己的问题和回答，就好比是非静态的，因为每个学生的问题都可能不同。
  
  在编程中，静态就是类级别的，它属于整个类而不是某个特定对象实例。静态变量和静态方法可以在不创建类的实例的情况下访问，就像在没有特定学生的情况下可以访问大黑板上的通用信息一样。而非静态的成员变量和方法则需要通过创建类的实例来访问，就像学生们需要提出自己的问题才能得
  到回答一样。*/
  ```
## 7.Number & Math

`https://www.runoob.com/java/java-number.html`

#### 1.总体介绍



Number这个类相当于把java中的所有内置数据类型都转换 成了**对象**的形式，使得这些对象能够有一些独特的属性

**Number属于lang包**，idea可以自动导入

![Java Number类](https://www.runoob.com/wp-content/uploads/2013/12/OOP_WrapperClass.png)

Java 的 Math 包含了用于执行基本数学运算的属性和方法，如初等指数、对数、平方根和三角函数。

**Math 的方法都被定义为 static 形式，通过 Math 类可以在主函数中直接调用。**这点很重要，不用实例化对象，也没有运用自动拆包

### 2.Number 的常用方法

#### 1.XXXValue()方法

- 不接受参数
- 返回的是原生的数据类型，不是Number里的对象

`https://www.runoob.com/java/number-xxxvalue.html`



```Java
public class Test{ 
 
   public static void main(String args[]){
      Integer x = 5;
      // 返回 byte 原生数据类型
      System.out.println( x.byteValue() );
 
      // 返回 double 原生数据类型
      System.out.println(x.doubleValue());
 
      // 返回 long 原生数据类型
      System.out.println( x.longValue() );      
   }
}
```

输出结果

```java
5
5.0
5

```

#### 2. compareTo()

```java
public int compareTo(NumberSubClass referenceName)
```

- 参数  可以是一个 Byte, Double, Integer, Float, Long 或 Short 类型的参数。
- 返回值
  - 如果指定的数与参数相等返回 0。
  - 如果指定的数小于参数返回 -1。
  - 如果指定的数大于参数返回 1。



实例

```java
public class Test{ 
   public static void main(String args[]){
      Integer x = 5;
      System.out.println(x.compareTo(3));
      System.out.println(x.compareTo(5));
      System.out.println(x.compareTo(8));            
     }
}

```

#### 3.equals()

`https://www.runoob.com/java/number-equals.html`

判断Number对象与方法的参数是否相等

语法 

```java
public boolean equals(object o)
```

相等则返回True否则返回False

#### 4.valueOf()

valueOf() 方法用于返回给定参数的原生 Number 对象值，参数可以是原生数据类型, String等。

该方法是静态方法。该方法可以接收两个参数一个是字符串，一个是基数。

 语法

该方法有以下几种语法格式：

```java
static Integer valueOf(int i)
static Integer valueOf(String s)
static Integer valueOf(String s, int radix)
```

参数

- **i** -- Integer 对象的整数。
- **s** -- Integer 对象的字符串。
- **radix** --在解析字符串 s 时使用的进制数，用于指定使用的进制数。

 返回值

- **Integer valueOf(int i)：**返回一个表示指定的 int 值的 Integer 实例。
- **Integer valueOf(String s):**返回保存指定的 String 的值的 Integer 对象。
- **Integer valueOf(String s, int radix):** 返回一个 Integer 对象，该对象中保存了用第二个参数提供的基数进行解析时从指定的 String 中提取的值。

```java
public class Test{ 
public static void main(String args[]){
                Integer x =Integer.valueOf(9);
                Double c = Double.valueOf(5);
                Float a = Float.valueOf("80");               

                Integer b = Integer.valueOf("444",16);   // 使用 16 进制

                System.out.println(x); 
                System.out.println(c);
                System.out.println(a);
                System.out.println(b);
        }
}
```



#### 5.toString()

toString() 方法用于返回以一个字符串表示的 Number 对象值。

如果方法使用了原生的数据类型作为参数，返回原生数据类型的 String 对象值。

如果方法有两个参数， 返回用第二个参数指定基数表示的第一个参数的字符串表示形式。

语法

以 String 类为例，该方法有以下几种语法格式：

```
String toString()
static String toString(int i)
```

**注意第二种方式为静态方法**,需要通过类来访问

参数

- **i** -- 要转换的整数。

返回值

- **toString():** 返回表示 Integer 值的 String 对象。
- **toString(int i):** 返回表示指定 int 的 String 对象。

实例

```java
public class Test{
    public static void main(String args[]){
        Integer x = 5;

        System.out.println(x.toString());  
        System.out.println(Integer.toString(12)); 
    }
}
```

编译以上程序，输出结果为：

```java
5
12
```

**自测实例二**

```java
public class temp3 {
    public static void main(String[] args) {
        Integer x = 10;
        Double x2=Double.valueOf(12.2);
        System.out.println(Integer.toString(123));
        System.out.println(x.getClass());
        System.out.println(x2.getClass());
        System.out.println(x2.toString().getClass());//返回的是String对象

    }
}

```

**运行结果**

```java
123
class java.lang.Integer
class java.lang.Double
class java.lang.String
```

#### 6.parseInt()

这个方法是把s转换为十进制

如果方法有两个参数， 使用第二个参数指定的基数，将字符串参数解析为有符号的整数。

语法

```java
static int parseInt(String s)

static int parseInt(String s, int radix)

```

**参数**

- s -- 表示十进制字符串
- radix 表示指定的进制数

**返回值**

- 第一个方法返回十进制，也就是默认十进制的整数值(int)，这个方法主要是把字符型数据转换为整型，**但是我感觉valueOf方法就平替了这个功能**
- 返回用于指定进制数的整数值

*当然这些方法也存在Double等其他Number的数据类型*

### 3.Math类的常用方法

#### 1.abs()

相对常见的一个方法，就是返回参数的绝对值

语法

```java
double abs(double d)
float abs(float f)
int abs(int i)
long abs(long lng)

```

参数

可以是任何原生数据类型

返回值 ：各种原生数据类型的绝对值

```java
public class Test{ 
    public static void main(String args[]){
        Integer a = -8;
        double d = -100;
        float f = -90f;    
                                                
        System.out.println(Math.abs(a));
        System.out.println(Math.abs(d));     
        System.out.println(Math.abs(f));    
    }
}
```



#### 2.round

表示四舍五入

```java
long round(double d)

int round(float f)

```



#### 3.max

返回两个较大的值

#### 4.min

返回两个较小的值

#### 5.random

返回一个随机数，random() 方法用于返回一个随机数，随机数范围为 0.0 =< Math.random < 1.0。

### 补充

#### 自动拆包问题

`Q`：

为什么我想使用Integer类创建一个Integer对象的时候不是用正常的用new来创建实例而是直接赋值

![image-20231011160348572](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231011160348572.png)

直接这样会报错

`解答`

在Integer类中存在了自动拆包

在Java中，对于 `Integer` 类和其他包装类（如 `Boolean`、`Byte`、`Short`、`Long`、`Float`、`Double`），提供了自动装箱（autoboxing）和自动拆箱（autounboxing）的特性。

自动装箱（autoboxing）是指Java编译器自动将基本数据类型转换为对应的包装类，而自动拆箱（autounboxing）是指将包装类自动转换为对应的基本数据类型。

所以，你可以直接赋值基本数据类型给包装类对象，Java会自动进行装箱，将基本数据类型转换为对应的包装类对象。

例如：

```java
Integer intValue = 42;  // 自动装箱，将int类型转换为Integer类型
```

这样就创建了一个 `Integer` 对象，其值为42。这种用法使代码更简洁，不需要显式使用 `new Integer(42)`。

同样，Java也支持自动拆箱。例如：

```java
int value = intValue;  // 自动拆箱，将Integer类型转换为int类型
```

这样将 `Integer` 对象转换为 `int` 值。

总结：你可以直接赋值基本数据类型给 `Integer` 对象，Java会自动进行装箱；你也可以将 `Integer` 对象直接赋值给基本数据类型，Java会自动进行拆箱。

#### 关于Number的静态方法

valueOf()是Number的一个静态方法，只能通过类来访问，不能通过实例来访问（所有实例都可用的上这个方法，所以设置为静态）

```java
//valueOf方法的具体实现
```

![image-20231011161203673](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231011161203673.png)

## 8.Character类



`https://www.runoob.com/java/java-character.html`

**常用方法**

- isLetter():判断是否是字幕
- isDigit():判断是否数字
- isWhitespace():判断是否是空白字符
- isUpperCase():判断是否是大写字母
- isLowerCase():判断是否是小写字母
- toUpperCase():转换为大写字母
- toLowerCase():转换为小写字母
- 

## 9.String类

`https://www.runoob.com/java/java-string.html`

api地址`https://www.apiref.com/java11-zh/java.base/java/lang/String.html`

java中String属于对象，String与Number类似，也提供

**注意:**String 类是不可改变的，所以你一旦创建了 String 对象，那它的值就无法改变了（详看笔记部分解析）

### length()方法求字符串长度

```java
public class StringDemo {
    public static void main(String args[]) {
        String site = "www.runoob.com";
        int len = site.length();
        System.out.println( "菜鸟教程网址长度 : " + len );
   }
}
```

### concat()

```java
public class StringDemo {
    public static void main(String args[]) {     
        String string1 = "菜鸟教程网址：";     
        System.out.println("1、" + string1 + "www.runoob.com");  
    }
}
```

```java
1、菜鸟教程网址：www.runoob.com

```

### 补充

![image-20231016170556205](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231016170556205.png)

## 10.StringBuffer & StringBuilder



### 介绍

由于字符串不可修改，使用StringBuffer和StringBuilider的对象可以修改

![img](https://www.runoob.com/wp-content/uploads/2013/12/java-string-20201208.png)

在使用 StringBuffer 类时，每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象，所以如果需要对字符串进行修改推荐使用 StringBuffer。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

由于 StringBuilder 相较于 StringBuffer 有速度优势，所以多数情况下建议使用 StringBuilder 类。

```java
public class RunoobTest{
    public static void main(String args[]){
        StringBuilder sb = new StringBuilder(10);
        sb.append("Runoob..");
        System.out.println(sb);  
        sb.append("!");
        System.out.println(sb); 
        sb.insert(8, "Java");
        System.out.println(sb); 
        sb.delete(5,8);
        System.out.println(sb);  
    }
}
```

​                               *流程图*



![img](https://www.runoob.com/wp-content/uploads/2013/12/2021-03-01-java-stringbuffer.svg)

二者的使用场景好像只是对线程安全度的考量StringBuffer对线程的安全度更高

以下是 StringBuffer 类支持的主要方法：

| 序号 | 方法描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | public StringBuffer append(String s) 将指定的字符串追加到此字符序列。 |
| 2    | public StringBuffer reverse()  将此字符序列用其反转形式取代。 |
| 3    | public delete(int start, int end) 移除此序列的子字符串中的字符。 |
| 4    | public insert(int offset, int i) 将 `int` 参数的字符串表示形式插入此序列中。 |
| 5    | insert(int offset, String str) 将 `str` 参数的字符串插入此序列中。 |
| 6    | replace(int start, int end, String str) 使用给定 `String` 中的字符替换此序列的子字符串中的字符。 |

以下列表列出了 StringBuffer 类的其他常用方法：

| 序号 | 方法描述                                                     |
| :--- | :----------------------------------------------------------- |
| 1    | int capacity() 返回当前容量。                                |
| 2    | char charAt(int index) 返回此序列中指定索引处的 `char` 值。  |
| 3    | void ensureCapacity(int minimumCapacity) 确保容量至少等于指定的最小值。 |
| 4    | void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin) 将字符从此序列复制到目标字符数组 `dst`。 |
| 5    | int indexOf(String str) 返回第一次出现的指定子字符串在该字符串中的索引。 |
| 6    | int indexOf(String str, int fromIndex) 从指定的索引处开始，返回第一次出现的指定子字符串在该字符串中的索引。 |
| 7    | int lastIndexOf(String str) 返回最右边出现的指定子字符串在此字符串中的索引。 |
| 8    | int lastIndexOf(String str, int fromIndex) 返回 String 对象中子字符串最后出现的位置。 |
| 9    | int length()  返回长度（字符数）。                           |
| 10   | void setCharAt(int index, char ch) 将给定索引处的字符设置为 `ch`。 |
| 11   | void setLength(int newLength) 设置字符序列的长度。           |
| 12   | CharSequence subSequence(int start, int end) 返回一个新的字符序列，该字符序列是此序列的子序列。 |
| 13   | String substring(int start) 返回一个新的 `String`，它包含此字符序列当前所包含的字符子序列。 |
| 14   | String substring(int start, int end) 返回一个新的 `String`，它包含此序列当前所包含的字符子序列。 |
| 15   | String toString() 返回此序列中数据的字符串表示形式。         |

#### 补充

1.

Java 中 StringBuffer 和 String 是有一定的区别的，首先，String 是被 final 修饰的，他的长度是不可变的，就算调用 String 的 concat 方法，那也是把字符串拼接起来并重新创建一个对象，把拼接后的 String 的值赋给新创建的对象，而 StringBuffer 的长度是可变的，调用StringBuffer 的 append 方法，来改变 StringBuffer 的长度，并且，相比较于 StringBuffer，String 一旦发生长度变化，是非常耗费内存的！

2.

String 长度大小不可变

StringBuffer 和 StringBuilder 长度可变

StringBuffer 线程安全 StringBuilder 线程不安全

StringBuilder 速度快

3.

##  11.Stream,file，io

![img](https://www.runoob.com/wp-content/uploads/2013/12/iostream2xx.png)

#### FileInputStream

该流用于从文件读取数据，它的对象可以用关键字 new 来创建。

```java
InputStream f = new FileInputStream("C:/java/hello");
```

也可以使用一个文件对象来创建一个输入流对象来读取文件，我们首先得使用File（）方法来创建一个文件对象

```java
File f = new File("C:/java/hello");
InputStrem fInput = new FielInputStrem(f);

```

创建了InputStream对象，就可以使用下面的方法来读取流或者进行其他的流操作。

实例

```java
import java.io.*;
 
public class fileStreamTest {
    public static void main(String[] args) {
        try {
            byte bWrite[] = { 11, 21, 3, 40, 5 };
            OutputStream os = new FileOutputStream("test.txt");
            for (int x = 0; x < bWrite.length; x++) {
                os.write(bWrite[x]); // writes the bytes
            }
            os.close();
 
            InputStream is = new FileInputStream("test.txt");
            int size = is.available();
 
            for (int i = 0; i < size; i++) {
                System.out.print((char) is.read() + "  ");
            }
            is.close();
        } catch (IOException e) {
            System.out.print("Exception");
        }
    }
}
```



### InputStrem常用的方法

| **序号** | **方法及描述**                                               |
| :------- | :----------------------------------------------------------- |
| 1        | **public void close() throws IOException{}** 关闭此文件输入流并释放与此流有关的所有系统资源。抛出IOException异常。 |
| 2        | **protected void finalize()throws IOException {}** 这个方法清除与该文件的连接。确保在不再引用文件输入流时调用其 close 方法。抛出IOException异常。 |
| 3        | **public int read(int r)throws IOException{}** 这个方法从 InputStream 对象读取指定字节的数据。返回为整数值。返回下一字节数据，如果已经到结尾则返回-1。 |
| 4        | **public int read(byte[] r) throws IOException{}** 这个方法从输入流读取r.length长度的字节。返回读取的字节数。如果是文件结尾则返回-1。 |
| 5        | **public int available() throws IOException{}** 返回下一次对此输入流调用的方法可以不受阻塞地从此输入流读取的字节数。返回一个整数值。 |

### OutputStrem常用方法

该类用来创建一个文件并向文件中写数据。

如果该流在打开文件进行输出前，目标文件不存在，那么该流会创建该文件。

有两个构造方法可以用来创建 FileOutputStream 对象。

使用字符串类型的文件名来创建一个输出流对象：

### OutputStrem的常用方法

```java
创建OutputStream 对象完成后，就可以使用下面的方法来写入流或者进行其他的流操作。

序号	方法及描述
1	public void close() throws IOException{}
关闭此文件输入流并释放与此流有关的所有系统资源。抛出IOException异常。
2	protected void finalize()throws IOException {}
这个方法清除与该文件的连接。确保在不再引用文件输入流时调用其 close 方法。抛出IOException异常。
3	public void write(int w)throws IOException{}
这个方法把指定的字节写到输出流中。
4	public void write(byte[] w)
把指定数组中w.length长度的字节写到OutputStream中。
```

实例

```java
//文件名 :fileStreamTest2.java
import java.io.*;
 
public class fileStreamTest2 {
    public static void main(String[] args) throws IOException {
 
        File f = new File("a.txt");
        FileOutputStream fop = new FileOutputStream(f);
        // 构建FileOutputStream对象,文件不存在会自动新建
 
        OutputStreamWriter writer = new OutputStreamWriter(fop, "UTF-8");
        // 构建OutputStreamWriter对象,参数可以指定编码,默认为操作系统默认编码,windows上是gbk
 
        writer.append("中文输入");
        // 写入到缓冲区
 
        writer.append("\r\n");
        // 换行
 
        writer.append("English");
        // 刷新缓存冲,写入到文件,如果下面已经没有写入的内容了,直接close也会写入
 
        writer.close();
        // 关闭写入流,同时会把缓冲区内容写入文件,所以上面的注释掉
 
        fop.close();
        // 关闭输出流,释放系统资源
 
        FileInputStream fip = new FileInputStream(f);
        // 构建FileInputStream对象
 
        InputStreamReader reader = new InputStreamReader(fip, "UTF-8");
        // 构建InputStreamReader对象,编码与写入相同
 
        StringBuffer sb = new StringBuffer();
        while (reader.ready()) {
            sb.append((char) reader.read());
            // 转成char加到StringBuffer对象中
        }
        System.out.println(sb.toString());
        reader.close();
        // 关闭读取流
 
        fip.close();
        // 关闭输入流,释放系统资源
 
    }
}
```

