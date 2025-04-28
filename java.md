# JavaSE



## 包

![image-20231204093828974](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204093828974.png)

如果出现有类名相同导致冲突，使用全类名创建对象

![image-20231204094251357](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204094251357.png)

## 1.ideal的使用

![image-20230512202424735](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230512202424735.png)

path环境变量配，可以用于命令行窗口打开应用程序

![image-20230512204201290](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230512204201290.png)

![image-20230512204729125](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230512204729125.png)

### 快捷键

选中需要的代码，ctrl+alt+t可以自动把代码放入一个死循环的while语句

![image-20230512205500647](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230512205500647.png)

![image-20230608110937574](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230608110937574.png)快捷遍历





![image-20230512210206189](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230512210206189.png)

alt+回车在对应的方法名可以自动创建一个方法

右键之后rename

删除文件的时候如果直接再idea deleate文件再创建相同工程名的工程时，会显示已经有过改工程，即使这个工程已经被删掉，所以建议直接在磁盘里面解决
	

### 如何打开工程

files->open	关闭工程可以直接关闭ide或者直接在file里面<u>close</u>

**debug**

![image-20230515165738430](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230515165738430.png)



## 2.数据类型

### 1.注释

与 c语言一样

![image-20230513195630966](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230513195630966.png)

*注释之所以不会影响程序的执行是因为最后编译的class文件里面不会包含注释*

![image-20230513195902382](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230513195902382.png)

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

![image-20230513202629578](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230513202629578.png)

##### 八进制，十六进制

![image-20230513203143375](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230513203143375.png)

```
System.out.println("money");
        int a=0141;
        System.out.println(a);
        int b=0xA;
        System.out.println(b);
        //再赋值的时候在前面加上0 表示八进制0x是十六进制
        
```

运行结果![image-20230513203502940](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230513203502940.png)

##### 数据大小

![image-20230513203727423](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230513203727423.png)

![image-20231126142412523](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231126142412523.png)

### 6.数据类型

![image-20230513204057800](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230513204057800.png)

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

![image-20231007190152867](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231007190152867.png)



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

![image-20230514025330881](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514025330881.png)



#### 在表达式中的转换

表达式中的最终结果又表达式中的最高类型决定

#### 强制转换

![image-20230514030712671](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514030712671.png)

强制转换的底层原理，可能存在精度丢失![image-20230514030846260](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514030846260.png)

### 运算符（主要列出与c语言不同的地方）

https://www.runoob.com/java/java-operators.html

#### "+"

***在做字符算运算的时候加号的作用是将两个字符串连接在一起*与c语言有很大不同**

![image-20230514031828597](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514031828597.png)

```Java
System.out.println("abc"+"c");
        System.out.println("abc"+5);
        int a=5,b=3;
        System.out.println(a+b);
        System.out.println("a"+5+"ji");
        //能算则算，不能算连接
```

![image-20230514032220018](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514032220018.png)

运行结果

#### 关系运算符

与c语言不同的是这边关系运算符的返回值是布尔值，true或者false,

![image-20230514110455849](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514110455849.png)

运算结果

```
true
false
```

#### 逻辑运算符

![image-20230514111150261](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514111150261.png)

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

![image-20230514111858864](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514111858864.png)

**按位或，按位与，按位异或，按位非这些运算符用的不多，与c语言类似，自己看就好**

#### 三元运算符

![image-20230514112010242](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514112010242.png)



```
a=100;
b=10;
System.out.println(a>b?a:b );
```

![image-20230514112436116](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514112436116.png)

了解就好，之后尽量用if语句

#### 运算符的优先级

记住一些比较特别的就好

1.双与的优先级大于双或(但是尽量还是不要用这个太多逻辑)

#### 键盘录入



![image-20230514183531769](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514183531769.png)





#### 补充

![image-20231010114025498](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231010114025498.png)

![image-20231010114346060](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231010114346060.png)

这个太细节了



![image-20231010114017870](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231010114017870.png)

![image-20231010113903183](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231010113903183.png)





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

![image-20230517104028826](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517104028826.png)

**需要注意的是随机数是0-n-1**



![*image-20230517104433436*](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517104433436.png)

***解决从n开始的随机数问题***

> **案例**
>
> *猜数字游戏*
>
> ## ![image-20230517104806894](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517104806894.png)
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
> ![image-20230514205311715](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514205311715.png)命名格式，其中new指的是创建一个新的东西 **一般用的是简化形式**
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
> ![image-20230514210816252](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514210816252.png)
>
> *同样跟c语言不同，不用借助库函数*

> ![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230514211022504.png)



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

![image-20230516141921312](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516141921312.png)



### 2.方法使用的常见问题

参考一下就好，感觉和函数差不多

![image-20230516143124805](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516143124805.png)



### 3.方法案例

### 4.方法调用的内存图

方法与方法之间可以互相调用

![image-20230516143821884](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516143821884.png)

![image-20230516144241399](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516144241399.png)

需要调用的时候再入栈，栈是先进后出



### 5.方法的参数传递机制

同样也是注意实参和形参。

![image-20230516144611365](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516144611365.png)



**引用类型的参数传递**

传递引用型变量的地址，因为引用的是地址，所以形参的改变也会是原参数的值改变，跟c语言的数组传递原理一样，数组名的本质就是地址

![image-20230516145155149](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516145155149.png)

**数组的元素存储再堆区**

​	

### 6.方法重载

**方法重载（overlode)的形式**

![image-20230516151102593](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516151102593.png)

![image-20230516151154581](D:\markdown\image-20230516151154581.png)

各种方法名字相同，但是参数和内容不同，不冲突

### return关键字

![image-20230516152138585](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230516152138585.png)

可以用于结束方法，上面的样例代码中分母的传入值如果等于零，就用return结束当前方法

### 方法的补充



## 6.面向对象

### 1.设计对象并使用

先设计类，再设计对象

![image-20230517110018870](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517110018870.png)

*如何设计类*

![image-20230517110233920](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517110233920.png)

![image-20230517110303056](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517110303056.png)

![image-20230517111003894](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517111003894.png)



**补充事项**

![image-20230517111333673](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517111333673.png)

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

![image-20230517113018211](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517113018211.png)

1.先把检索到的类放进方法去

2.把main方法放入栈区

3.对应变量加载进栈内存

4.对象的内存地址放入堆区

![image-20230517113509658](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517113509658.png)

总结

![image-20230517113647488](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230517113647488.png)





#### 两个变量指向同一个对象内存图

当两个对象相同，修改一个对象的属性，另外一个指向相同对象的属性也会被改

![image-20231129083808704](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129083808704.png)

### 3.构造器

构造的时候就是个对象初始化参数，没有构造方法系统会有个默认赋值初始值的方法

**构造方法是在new的时候创建的**

构造方法允许重载   ------------------*不重载要你也没鸟用。。。*



![image-20231129090457461](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129090457461.png)

#### 执行流程

![image-20231129091056070](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129091056070.png)

在new的时候new会在堆内存中开辟一串地址和默认值，之后Student（）这个构造会寻找并且调用对应参数的构造方法，把该方法调用到栈内存中，之后构造方法会在堆内存中初始化Student的属性

![image-20231129091233621](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129091233621.png)

初始化完之后，构造方法出栈桥，构造过程结束，**并且把之前new出来的内存地址传给stu**

new是用来开辟地址！

Student()是用来初始化！





### 4.this关键词



 当你直接答应this的时候，print的就是这个对象的内存地址

![image-20231129090333074](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129090333074.png)	

### 5.封装

![image-20231129092208779](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129092208779.png)

封装的设计规范

合理隐藏，合理暴露

用private把savelog隐藏起来，藏到call里面

![image-20231129092515371](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129092515371.png)

封装过程中给私用的成员变量提供运用合理规则的public方法，方法来保证数据安全



### 6.标准JavaBean

![image-20231129094545031](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129094545031.png)

实体类----------**只负责数据的存取**

1. 成员变量私有化
2. 有空参，带参数的构造方法
3. 对于私有成员变量，提供对应的setXXX和getXXX方法

*set和get在idea有对应的插件可以快捷键生成*，也可以通过通过ptg插件一键生成





### 权限修饰符

private : 同一个类中

 (default) : 同一个类中, 同一个包中

protected : 同一个类中, 同一个包中, 不同包的子类

TODO: 继承

 public : 任意位置访问，**可以垮包**

### 7.补充知识：成员变量，局部变量区别



![image-20231129083955947](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129083955947.png)

​		成员变量可能被多个进程同时使用，所以需要存放在堆内存中

![image-20231129084405928](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231129084405928.png)



### static

是所有对象共有的成员变量

![image-20231203170204494](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231203170204494.png)

#### static内存地址地址的解析

![image-20231203170749228](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231203170749228.png)

### 继承

![image-20231203182623078](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231203182623078.png)

![image-20231203182837472](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231203182837472.png)

子父类的名字重复，使用最近原则

#### 子类的方法重写

如果方法名字相同，参数或者返回值不同是重载！

可以使用@overload表示重载

@override表示重写

![image-20231203185054047](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231203185054047.png)

所有子类的构造方法**第一句**当中都有super()这句语句，父类中也有super()，一直到最顶层的object类

想调用父类的构造方法也只能放在第一句

### fianl

![image-20231204090138251](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204090138251.png)

![image-20231204090202885](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204090202885.png)

### 8.面向对象综合案例

**1.案例（购物车）**

![image-20230608105516671](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230608105516671.png)

![image-20230608105649691](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230608105649691.png)



![image-20230608112226691](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20230608112226691.png)

构造方法无法继承

 

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

- 形参与成员名字重名，用this来区分，**若不是使用this打印的就是形参的值**

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
### 10.抽象类

抽象方法需要在抽象类中定义，抽象类的子类需要对抽象方法进行重写

![image-20231204095122107](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204095122107.png)

![image-20231204094917753](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204094917753.png)

书写的格式

![image-20231204095151835](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204095151835.png)

抽象类中有构造方法，提供给子类使用super访问，普通的方法同样可以存在也是让子类使用super继承

一些注意事项

![image-20231204154621983](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204154621983.png)

### 接口

全部都是抽象方法的抽象类------***在声明规则***

没有成员变量，没有普通方法

![image-20231204155430244](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204155430244.png)

![image-20231204155515715](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204155515715.png)

#### 总体介绍

通过implement来通过接口类来重现抽象方法

implement相当于就是接口的子类 

![image-20231204155810585](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204155810585.png)

接口的实现一半是通过重写所有的抽象方法，而不是再次定义为一个抽象类

#### 接口的成员特点

- 接口中没有构造方法，子类的构造方法中的super访问的是object类

- 成员变量只能定义常量，这个常量被public static final三个修饰符修饰

- 成员方法，只能是抽象方法----------------`public abstract` 

  ​								*系统会自动对方法添加public abstract 这两个关键字*

![image-20231204161913431](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204161913431.png)

接口与类可以多实现，同时实现两个接口，这点与继承不同，而且不存在逻辑冲突（方法同名），**甚至可以在继承的同时实现接口**

![image-20231204162339089](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204162339089.png)

**继承是类与类之间的单继承** 

#### 抽象类和接口的对比

抽象类的应用场景，

抽象类时对事物的描述-------------*对事物做抽象*

![image-20231204162518247](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204162518247.png)

![image-20231204162446466](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204162446466.png)

接口的场景，制定规则-----------------------*对行为做抽象*

![image-20231204162635432](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204162635432.png)

### 11.多态

提高代码的扩展性 

![image-20231204163524180](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204163524180.png)

#### 多态的前提

![image-20231204163631896](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204163631896.png)

1.对象多态

![image-20231204163831369](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204163831369.png)

2.行为多态

![image-20231204164038070](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204164038070.png)

#### 多态的成员访问特点

调用成员变量调用的是父类的成员变量

成员方法调用的是子类的成员方法 

![image-20231204165420950](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204165420950.png)

**特别的**，静态的成员是调用父类的对象

多态的形式创建对象，不**能调用子类的特有成员**（因为需要检查父类是否拥有这个方法），需要使用多态的转型

#### 转型

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204170402126.png)

转型的过程中可能会存在一些类型冲突

![image-20231204170858771](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231204170858771.png)

### 内部类

内部类就是在定义在一个类里面的类

![image-20231205165521030](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205165521030.png)

#### 静态内部类

静态内部类的创建对象方式

![image-20231205170220820](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205170220820.png)

  ![image-20231205170936867](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205170936867.png)

#### 成员内部类

*JDK16之前不让编写静态成员*

**属于外部类的一个对象！！** 

![image-20231205171137740](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205171137740.png)

![image-20231205172054184](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205172054184.png)

```java
//heartbeat
//this.heartbeat
//People.this.heartbeat
```

#### 局部内部类

局部内部类放在方法，乃买快，构造方法等执行体中

局部内部咧的类文件名文：外部咧$N内部咧.class

![image-20231205172317734](/Users/xiechen/Library/Application Support/typora-user-images/image-20231205172317734.png)

#### 匿名内部类（重点）

本质上是一个没有名字的局部内部类

![image-20231205173041980](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205173041980.png)

案例

下面这个案例利用了匿名内部类来省去了老虎这个子类

```java
public class Test {
    public static void main(String[] args) {
        Animal a = new Animal(){			//直接不用创建老虎这个子类
            @Override
            public void run() {
                System.out.println("老虎跑的块~~~");
            }
        };
        a.run();
    }
}

//class Tiger extends Animal{
//    @Override
//    public void run() {
//        System.out.println("老虎跑的块~~~");
//    }
//}

abstract class Animal{
    public abstract void run();
}
```

##### 匿名内部类的真实使用场景



## 7.Number & Math

`https://www.runoob.com/java/java-number.html`

#### 1.总体介绍

![image-20231208090241183](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208090241183.png)

![image-20231208090425965](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208090425965.png)

![image-20231208090502115](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208090502115.png)

包装类同样重写了toString方法

Number这个类相当于把java中的所有内置数据类型都转换 成了**对象**的形式，使得这些对象能够有一些独特的属性

**Number属于lang包**，idea可以自动导入

![Java Number类](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/OOP_WrapperClass.png)

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

![image-20231011160348572](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231011160348572.png)

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

#### ceil

向下取整

![image-20231205201534044](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205201534044.png)

#### 关于Number的静态方法

valueOf()是Number的一个静态方法，只能通过类来访问，不能通过实例来访问（所有实例都可用的上这个方法，所以设置为静态）

```java
//valueOf方法的具体实现
```

![image-20231011161203673](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231011161203673.png)

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

输出的是False，由于s1和s2都是对象，所以比较的是内存地址，通过+号拼接的字符串是通过调用其他类的方法拼接而成最后在堆内存中新建一个地址，最后交给s3

![image-20231130095240505](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231130095240505.png)

下面这个例子输出的是true，因为是三个字符串常量，对于常量的相互拼接java中的内存优化机制会将其转换到String池中对应的对象地址

![image-20231130095515373](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231130095515373.png)

`https://www.runoob.com/java/java-string.html`

api地址`https://www.apiref.com/java11-zh/java.base/java/lang/String.html`

java中**String属于对象**，String与Number类似，也提供

**注意:**String 类是不可改变的，所以你一旦创建了 String 对象，那它的值就无法改变了（详看笔记部分解析）

！！注意，String是对象，相同的对象属性会使不同名字的String指向相同地址

通过构造方法创建的字符串对象会在堆内存中有自己的空间，而不是在字符串池当中，若创建的对象在字符串池中存在，则拷贝一份副本（地址）到自己的堆内存中

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

### 字符串比较

public boolean equals(String otherString)

比较的是字符串的内容，由于字符串是对象，之间用逻辑运算符判断的话判断的是对象的内存地址是否相同

public boolean equalsIgnoreCase(String anotherString) 将此 String 与另一个 String 比较，不考虑大小写。

用这个方法可以忽略大小写，可以用于验证码忽略大小写

### 字符串的索引遍历

- public char[] toCharArray ()  将字符串转换为字符数组 

- **public char chatAt (int index) 根据索引找字符** ------------*感觉这个最好用*

- public int length() : 返回字符串的长度


### 字符串的截取，替换

```java
public String substring(int beginIndex, int endIndex)     
public String substring(int beginIndex)     
  
  //需要注意的是他是返回一个字符串对象，而不是改变原来的字符串！ 注意函数的返回类型就好
```





```java
public String replace(旧值,新值)  
```



### **切割**

这个split方法与python中的split差不多感觉。。



```java
//@para regex  替换的标示
public String[] split(String regex) ：
//根据传入的字符串作为规则进行切割
//将切割后的内容存入字符串数组中，并将字符串数组返回

```



### 补充

![image-20231016170556205](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231016170556205.png)





## Object类

![image-20231205183515198](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205183515198.png)

### 常用方法

![image-20231205183609407](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205183609407.png)

toString就是直接print对象名字能够输出对象地址的原因，直接打印的时候toString省略了

**父类toString()方法存在的意义就是为了被子类重写，以便返回对象的内容信息，而不是地址信息！！**

**equals同样存在的意义也是被子类重写，就像String中的equals**---------------*将地址相同转换成内容相同*



重写toString可以指定子类的打印内容

java中比较字符串相同是用Objects类的equals方法，更安全

```java
public class Test {
    public static void main(String[] args) {
        String s1 = null;
        String s2 = new String("itheima");

        // System.out.println(s1.equals(s2));   // 留下了隐患，可能出现空指针异常。

        System.out.println(Objects.equals(s1, s2)); // 更安全，结果也是对的！

        /**
        		java官方JDK实现
             Objects：
             public static boolean equals(Object a, Object b) {
                     return (a == b) || (a != null && a.equals(b));--------比较了是否是null
             }
         */

        System.out.println(Objects.isNull(s1)); // true
        System.out.println(s1 == null); // true

        System.out.println(Objects.isNull(s2)); // false
        System.out.println(s2 == null); // false

    }
}
```



![image-20231205195043147](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205195043147.png)

总结

![image-20231205195234402](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205195234402.png)

##  10.StringBuffer & StringBuilder

**一般直接使用StringBuilder，而且操作的时间复杂度会更低**

![image-20231130180130218](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231130180130218.png)

官方api文档

其中第一种的空参传入即使超出16个字符也会自动扩容

![image-20231130180424215](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231130180424215.png)

### 介绍



补充一个好用的方法

`public StringBulider reverse()`

toString可以吧StringBulider中没用的方法转换成字符串用字符串的方法来实现

**由于字符串不可修改，使用StringBuffer和StringBuilider的对象可以修改**

![img](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/java-string-20201208.png)

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

#### 常用方法图

![image-20231130180756023](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231130180756023.png)

![img](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/2021-03-01-java-stringbuffer.svg)

二者的使用场景好像只是对线程安全度的考量StringBuffer对线程的安全度更高

**以下是 StringBuffer 类支持的主要方法：**

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

## System类

时间的初始值是C语言的诞生时间

```java
/**1.public static void exit(int status):终止JVM虚拟机，非0是异常终止。
        2.public static long currentTimeMillis():获取当前系统此刻时间毫秒值。(重点)
        3.可以做数组的拷贝。
             arraycopy(Object var0, int var1, Object var2, int var3, int var4);
             * 参数一：原数组
             * 参数二：从原数组的哪个位置开始赋值。
             * 参数三：目标数组
             * 参数四：赋值到目标数组的哪个位置？
             * 参数五：赋值几个。
             */
```

## BigDecimal类





*解决浮点数失真*

具体使用自行查询API文档

计算完成之后可以用BigDecimal的方法把BigDecimal的对象转换成想要对应的数据类型



![image-20231205202036872](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231205202036872.png)

如果需要计算的数据不需要精度运算，会报错

实例

```java
				BigDecimal a11 = BigDecimal.valueOf(10.0);
        BigDecimal b11 = BigDecimal.valueOf(3.0);
        /**
           参数一：除数 参数二：保留小数位数  参数三：舍入模式
         */
        BigDecimal c11 = a11.divide(b11, 2, RoundingMode.HALF_UP); // 3.3333333333
        System.out.println(c11);
```



##  11.Stream,file，io

### 字符集

![image-20240108202648888](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108202648888.png)

### File类

![image-20240108192743817](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108192743817.png)

#### 常用aip

![image-20240108192844995](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108192844995.png)

这个创建文件夹一般感觉只适用于创建脚本，不然实用性都不如直接打开终端mkdir![image-20240108194047494](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108194047494.png)





用list取当前目录文件的时候，会存在一些情况为返回值为null的，需要注意，**空白文件夹返回长度为0的数组**，一般是获取文件数组对象的情况较为常见

![File的遍历](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108195152072.png)

由于上述的遍历方式只能遍历一级目录，java没有提供递归创建的api，应当自行编写，一个很简答的递归，最小的基本情况就是找到对应的路径，用一个if来判断文件名字，下面是一个递归搜索的实例

```java

import java.io.File;
import java.io.IOException;

/**
    目标：去D判断搜索 eDiary.exe文件
 */
public class RecursionDemo05 {
    public static void main(String[] args) {
        // 2、传入目录 和  文件名称
        searchFile(new File("D:/") , "eDiary.exe");
    }

    /**
     * 1、搜索某个目录下的全部文件，找到我们想要的文件。
     * @param dir  被搜索的源目录
     * @param fileName 被搜索的文件名称
     */
    public static void searchFile(File dir,String fileName){
        // 3、判断dir是否是目录
        if(dir != null && dir.isDirectory()){
            // 可以找了
            // 4、提取当前目录下的一级文件对象
            File[] files = dir.listFiles(); // null  []
            // 5、判断是否存在一级文件对象，存在才可以遍历
            if(files != null && files.length > 0) {
                for (File file : files) {
                    // 6、判断当前遍历的一级文件对象是文件 还是 目录
                    if(file.isFile()){
                        // 7、是不是咱们要找的，是把其路径输出即可
                        if(file.getName().contains(fileName)){
                            System.out.println("找到了：" + file.getAbsolutePath());
                            // 启动它。
                            try {
                                Runtime r = Runtime.getRuntime();
                                r.exec(file.getAbsolutePath());
                            } catch (IOException e) {
                                e.printStackTrace();
                            }
                        }
                    }else {
                        // 8、是文件夹，需要继续递归寻找
                        searchFile(file, fileName);
                    }
                }
            }
        }else {
            System.out.println("对不起，当前搜索的位置不是文件夹！");
        }
    }
}
```



![img](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/iostream2xx.png)

### I/O

![io类型](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108202450843.png)

![四大类](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108202543375.png)

![继承关系](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108202841855.png)

#### InputStream

第二个构造器实质上是在源码里面通过路径来床一个File对象然后再用第一个构造器来构造FileInputStream对象

**read方法读取结束之后会返回-1**，可以读取字节数组或者一个字节

![image-20240108203051131](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108203051131.png)

下面是用read读取字节流，以数组的形式读取，数组的大小代表一次读取的多少，下面实例一次读取三个字节，但是如过字节大小不能整除，需要设置

![image-20240108204931574](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108204931574.png)

```java
import java.io.FileInputStream;
import java.io.InputStream;
/**
   目标：使用文件字节输入流每次读取一个字节数组的数据。
 */
public class FileInputStreamDemo02 {
    public static void main(String[] args) throws Exception {
        // 1、创建一个文件字节输入流管道与源文件接通
        InputStream is = new FileInputStream("file-io-app/src/data02.txt");

        // 2、定义一个字节数组，用于读取字节数组
//        byte[] buffer = new byte[3]; // 3B
//        int len = is.read(buffer);
//        System.out.println("读取了几个字节：" + len);
//        String rs = new String(buffer);
//        System.out.println(rs);
//
//        int len1 = is.read(buffer);
//        System.out.println("读取了几个字节：" + len1);
//        String rs1 = new String(buffer);
//        System.out.println(rs1);
//        // buffer = [a b c]
//
//        // buffer = [a b c]  ==>  [c d c]
//        int len2 = is.read(buffer);
//        System.out.println("读取了几个字节：" + len2);
//        // 读取多少倒出多少
//        String rs2 = new String(buffer,0 ,len2);
//        System.out.println(rs2);
//
//        int len3 = is.read(buffer);
//        System.out.println(len3); // 读取完毕返回-1

        // 3、改进使用循环，每次读取一个字节数组
        byte[] buffer = new byte[3];
        int len; // 记录每次读取的字节数。
        while ((len = is.read(buffer)) != -1) {
            // 读取多少倒出多少
          
          //System.out.print(new String(buffer, 0 , len)); - 这一行代码将从输入流中读取的字节数组 buffer 中的数据转换为字符串，并打印出来。这里使用了 new String(buffer, 0, len) 来创建一个新的字符串，从 buffer 数组的索引0开始，长度为 len 的部分。这样可以确保只打印实际读取的字节数，避免打印未使用的部分
            System.out.print(new String(buffer, 0 , len));
        }
    }
}
```



但是上面代码读取文件的时候还是会遇到读取中文（3字节）会乱麻的问题，所以字节流用于读取文本不是很合理，可以使用字符流来读取文本内容，或者使用较大的字节数组来一次性读取文本（f.length），防止不一样的字符集大小引起的乱码问题。



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



##### FileInputStrem常用的方法

| **序号** | **方法及描述**                                               |
| :------- | :----------------------------------------------------------- |
| 1        | **public void close() throws IOException{}** 关闭此文件输入流并释放与此流有关的所有系统资源。抛出IOException异常。 |
| 2        | **protected void finalize()throws IOException {}** 这个方法清除与该文件的连接。确保在不再引用文件输入流时调用其 close 方法。抛出IOException异常。 |
| 3        | **public int read(int r)throws IOException{}** 这个方法从 InputStream 对象读取指定字节的数据。返回为整数值。返回下一字节数据，如果已经到结尾则返回-1。 |
| 4        | **public int read(byte[] r) throws IOException{}** 这个方法从输入流读取r.length长度的字节。返回读取的字节数。如果是文件结尾则返回-1。 |
| 5        | **public int available() throws IOException{}** 返回下一次对此输入流调用的方法可以不受阻塞地从此输入流读取的字节数。返回一个整数值。 |

#### OutPutStream

![image-20240108205442069](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108205442069.png)

写数据的api

![image-20240108205512333](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108205512333.png)

##### OutputStrem常用方法

![image-20240108211159064](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108211159064.png)

该类用来创建一个文件并向文件中写数据。

如果该流在打开文件进行输出前，目标文件不存在，那么该流会创建该文件。

有两个构造方法可以用来创建 FileOutputStream 对象。

使用字符串类型的文件名来创建一个输出流对象：



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

实例1

```java
package FileOotDemo;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.OutputStream;

public class FileOutPutStreamDemo1 {
    public static void main(String[] args) throws Exception {
        //创建一个文件，true使如果父目录不存在会自动创建目录，并且开启追加模式
        //如果不是true每次创建管道都会删除原数据
        OutputStream txtDemo = new FileOutputStream("/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/se/0、JavaSE进阶主课程/day08、日志框架、阶段项目/FileMod/textDemo.txt",true);

        //写入数据，默认写入一个数据，也可以写入一个字节数组
        txtDemo.write('h');
        txtDemo.write('7');

        //刷新管道
        txtDemo.flush();

        //最后要关闭管道
        txtDemo.close();
    }
}
```

实例2

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

### 文件的拷贝（适合用于视频的拷贝）

```java
package FileCopy;
//拷贝了一个音频文件
import java.io.*;
import java.util.function.IntPredicate;

public class copyFile {
    public static void main(String[] args) {
        try{
            //获取字节输入管道
            InputStream is = new FileInputStream("/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/se/0、JavaSE进阶主课程/day08、日志框架、阶段项目/视频/08、影片下架、修改、展示排片信息，用户购票.mp4");

            //创建一个输出管道
            OutputStream os = new FileOutputStream("/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/se/0、JavaSE进阶主课程/day08、日志框架、阶段项目/FileMod/new.avi");

            //定义一个字节数组转移数据
            byte[] buffer = new byte[1024];
            int len;
            while ((len = is.read(buffer)) != -1){
                os.write(buffer,0,len);
            }
            System.out.println("copy successful!");
            os.close();
            is.close();
        }catch (Exception e){
            e.printStackTrace();
        }


    }
}
```

### try-catch-finally释放资源

使用这样处理异常的好处就是防止程序中途错误最后没有关闭管道

![image-20240108212736817](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108212736817.png)

但是这样过于繁琐，再介绍一种,try里面定义的流对象在用完之后会自动销毁

可以自己写一个数据类然后继承AutoCloseAble接口，这样就可以吧对象自定义成可销毁对象

![image-20240108220248999](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108220248999.png)

![image-20240108220105697](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108220105697.png)

这是jdk7改进写法（常用）

![image-20240108220515486](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108220515486.png)

jdk9的写法，可以吧定义的语句放在try外面，只在try括号里放入需要销毁的对象，但是由于吧定义放在了try外面，最后还是要在main函数外面抛出异常

![image-20240108220634382](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108220634382.png)

### 字符流的使用

由于读取的是字符，可以防止读取不同字节大小的字符的时候不会乱码，但是他返回的也是int类型的字节数字，若想要看字符，还是要转换为char类型的字符

继承关系

![image-20240108220826614](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108220826614.png)

#### Reader（字符输入流）

reader同样也是抽象类，无法直接使用，需要实例化FileReader对象

##### FileReader

常用api，与FileInputStream一样，也可以输入的是字符数组，自定义读取多少个字符

![image-20240108221034085](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108221034085.png)

下面是读取一个字符的实例

```java
package com.itheima.d6_char_stream;

import java.io.File;
import java.io.FileReader;
import java.io.Reader;

/**
     目标：字符输入流的使用。

     IO流的体系：
            字节流                                   字符流
     字节输入流           字节输出流               字符输入流       字符输出流
     InputStream         OutputStream            Reader         Writer     (抽象类)
     FileInputStream     FileOutputStream        FileReader     FileWriter (实现类)

     c.FileReader:文件字符输入流。
         -- 作用：以内存为基准，把磁盘文件的数据以字符的形式读入到内存。
            简单来说，读取文本文件内容到内存中去。

         -- 构造器：
            public FileReader(File file):创建一个字符输入流与源文件对象接通。
            public FileReader(String filePath):创建一个字符输入流与源文件路径接通。

         -- 方法：
            public int read(): 读取一个字符的编号返回！ 读取完毕返回-1
            public int read(char[] buffer):读取一个字符数组，读取多少个字符就返回多少个数量，读取完毕返回-1
     小结：
        字符流一个一个字符的读取文本内容输出，可以解决中文读取输出乱码的问题。
        字符流很适合操作文本文件内容。
        但是：一个一个字符的读取文本内容性能较差！！
 */
public class FileReaderDemo01 {
    public static void main(String[] args) throws Exception {
        // 目标：每次读取一个字符。
        // 1、创建一个字符输入流管道与源文件接通
        Reader fr = new FileReader("file-io-app\\src\\data06.txt");

        // 2、读取一个字符返回，没有可读的字符了返回-1
//        int code = fr.read();
//        System.out.print((char)code);
//
//        int code1 = fr.read();
//        System.out.print((char)code1);

        // 3、使用循环读取字符
        int code;
        while ((code = fr.read()) != -1){
            System.out.print((char) code);
        }
    }
}
```

读取字符型数组的实例

```java
public class FileReaderDemo02 {
    public static void main(String[] args) throws Exception {
        // 1、创建一个文件字符输入流与源文件接通
        Reader fr = new FileReader("file-io-app/src/data07.txt");

        // 2、用循环，每次读取一个字符数组的数据。  1024 + 1024 + 8
        char[] buffer = new char[1024]; // 1K字符
        int len;
        while ((len = fr.read(buffer)) != -1) {
            String rs = new String(buffer, 0, len);
            System.out.print(rs);
        }

    }
}
```

#### Writer

同样是抽象类，需要创建具体的实现类对象来使用

##### FileWriter

构造器

![image-20240108221917968](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108221917968.png)

常用的api

![image-20240108221951467](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240108221951467.png)

**字符流的使用之后同样也是需要进行管道关闭**

### 缓冲流

继承关系

![image-20240112144805384](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112144805384.png)

字节缓冲流构造器

![image-20240112145219744](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112145219744.png)

多态构造（默认8kb缓冲）![image-20240112145333556](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112145333556.png)

使用方法与InputStream是相同的

**字符流缓冲流也是相似与Reader与Wirter**

字符缓冲输入流新增了readLine功能，可以一次读一行的代码（注意这样不能使用多态）

字符缓冲输出流也多了个newLine功能

```java
package com.itheima.d3_char_buffer;

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.Writer;

/**
     目标：缓冲字符输出流的使用，学会它多出来的一个功能：newLine();
 */
public class BufferedWriterDemo2 {
    public static void main(String[] args) throws Exception {
        // 1、创建一个字符输出流管道与目标文件接通
        Writer fw = new FileWriter("io-app2/src/out02.txt"); // 覆盖管道，每次启动都会清空文件之前的数据
       //Writer fw = new FileWriter("io-app2/src/out02.txt", true); // 追加数据
        BufferedWriter bw = new BufferedWriter(fw);

//      a.public void write(int c):写一个字符出去
        bw.write(98);
        bw.write('a');
        bw.write('徐'); // 不会出问题了
        bw.newLine(); // bw.write("\r\n"); // 换行

//       b.public void write(String c)写一个字符串出去
        bw.write("abc我是中国人");
        bw.newLine(); // bw.write("\r\n"); // 换行


//       c.public void write(char[] buffer):写一个字符数组出去
        char[] chars = "abc我是中国人".toCharArray();
        bw.write(chars);
        bw.newLine(); // bw.write("\r\n"); // 换行


//       d.public void write(String c ,int pos ,int len):写字符串的一部分出去
        bw.write("abc我是中国人", 0, 5);
        bw.newLine(); // bw.write("\r\n"); // 换行

//       e.public void write(char[] buffer ,int pos ,int len):写字符数组的一部分出去
        bw.write(chars, 3, 5);
        bw.newLine(); // bw.write("\r\n"); // 换行


        // fw.flush();// 刷新后流可以继续使用
        bw.close(); // 关闭包含刷线，关闭后流不能使用

    }
}
```

![image-20240112150852201](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112150852201.png)

![image-20240112150912499](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112150912499.png)

### 转换流

解决代码编码和文件编码不一致

![image-20240112154602749](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112154602749.png)

![image-20240112155241299](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112155241299.png)

**继承于Reader，解决流程就是提取原有的编码流，然后转乘自定义字符流（构造方法传入对应的参数）**

实例

```java
import java.io.*;

/**
     目标：字符输入转换流InputStreamReader的使用。

             字节流                                     字符流
     字节输入流               字节输出流              字符输入流            字符输出流
     InputStream             OutputStream          Reader               Writer   (抽象类)
     FileInputStream         FileOutputStream      FileReader           FileWriter(实现类)
     BufferedInputStream     BufferedOutputStream  BufferedReader       BufferedWriter(实现类，缓冲流)
                                                   InputStreamReader    OutputStreamWriter
     字符输入转换流InputStreamReader:
          -- 作用：可以解决字符流读取不同编码乱码的问题。
                  也可以把原始的字节流按照指定编码转换成字符输入流

          -- 构造器：
                public InputStreamReader(InputStream is)：可以使用当前代码默认编码转换成字符流，几乎不用！
                public InputStreamReader(InputStream is,String charset):可以指定编码把字节流转换成字符流(核心)

     小结：
        字符输入转换流InputStreamReader:作用：可以解决字符流读取不同编码乱码的问题。
        public InputStreamReader(InputStream is,String charset):可以指定编码把字节流转换成字符流(核心)
 */
public class InputStreamReaderDemo01 {
    public static void main(String[] args) throws Exception {
        // 代码UTF-8   文件 GBK  "D:\\resources\\data.txt"
        // 1、提取GBK文件的原始字节流。   abc 我
        //                            ooo oo
        InputStream is = new FileInputStream("D:\\resources\\data.txt");
        // 2、把原始字节流转换成字符输入流
        // Reader isr = new InputStreamReader(is); // 默认以UTF-8的方式转换成字符流。 还是会乱码的  跟直接使用FileReader是一样的
        Reader isr = new InputStreamReader(is , "GBK"); // 以指定的GBK编码转换成字符输入流  完美的解决了乱码问题

        BufferedReader br = new BufferedReader(isr);
        String line;
        while ((line = br.readLine()) != null){
            System.out.println(line);
        }
    }
}
```

同样字符输出转换流也可以进行转换，这里就不列出来了

### 序列化（输出输入对象）

Object流属于高级流，构造时传入的是低级流来构建，详情参照下面的构造方法

![image-20240112160230788](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112160230788.png)



序列化的时候可以给对象添加版本号信息，版本号是最后添加，根据类里面的成员变量生成的一个唯一的版本号

![image-20240112163433688](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112163433688.png)

![构造器](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112160408483.png)

实例图

同时，**对象要序列化必须实现Serializable接口**!

先实现接口

补充

被translient修饰的成员变量不会被序列化，可以防止敏感信息的泄漏

![transilent](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112162050154.png)

![image-20240112161209821](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112161209821.png)

![image-20240112161045571](/Users/xiechen/Library/Application Support/typora-user-images/image-20240112161045571.png)



同时也有反序列化
ObjectInputStream

![image-20240112162240793](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112162240793.png)

反序列化的过程就是将文件中的对象恢复到java的程序中去

![image-20240112161801664](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112161801664.png)

### 打印流

继承关系

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112164644547.png)

很好用！

![image-20240112164215208](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112164215208.png)

```java
package com.itheima.d6_printStream;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.PrintStream;
import java.io.PrintWriter;

/**
    目标：学会使用打印流 高效  方便写数据到文件。
 */
public class PrintDemo1 {
    public static void main(String[] args) throws Exception {
        // 1、创建一个打印流对象
//        PrintStream ps = new PrintStream(new FileOutputStream("io-app2/src/ps.txt"));
//        PrintStream ps = new PrintStream(new FileOutputStream("io-app2/src/ps.txt" , true)); // 追加数据，在低级管道后面加True
//        PrintStream ps = new PrintStream("io-app2/src/ps.txt" );
        PrintWriter ps = new PrintWriter("io-app2/src/ps.txt"); // 打印功能上与PrintStream的使用没有区别

        ps.println(97);
        ps.println('a');
        ps.println(23.3);
        ps.println(true);
        ps.println("我是打印流输出的，我是啥就打印啥");

        ps.close();
    }
}
```

字节打印流的api![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112164959164.png)

打印流的追加功能需要添加到他的低级管道去，他自身加true的作用是autoflush

#### 打印流的重定向

```java
class PrintDemo2 {
    public static void main(String[] args) throws Exception {
        System.out.println("锦瑟无端五十弦");
        System.out.println("一弦一柱思华年");

        // 改变输出语句的位置（重定向）
        PrintStream ps = new PrintStream("io-app2/src/log.txt");
        System.setOut(ps); // 把系统打印流改成我们自己的打印流

      //这两句会答应在ps的管道里
        System.out.println("庄生晓梦迷蝴蝶");
        System.out.println("望帝春心托杜鹃");
    }
}
```

### Properties

![image-20240112170248309](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112170248309.png)

![image-20240112170303840](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112170303840.png)

主要掌握通过properties存储键值对

这里面的取键的方法不是get而是getproperties（） 

同样设置不是put而是setproperties

![image-20240112170559325](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112170559325.png)

![image-20240112170408004](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112170408004.png)

实例代码

```java
class PropertiesDemo01 {
    public static void main(String[] args) throws Exception {
        // 需求：使用Properties把键值对信息存入到属性文件中去。
        Properties properties = new Properties();
        properties.setProperty("admin", "123456");
        properties.setProperty("dlei", "003197");
        properties.setProperty("heima", "itcast");
        System.out.println(properties);

        /**
           参数一：保存管道 字符输出流管道
           参数二：保存心得
         */
        properties.store(new FileWriter("io-app2/src/users.properties")
                , "this is users!! i am very happy! give me 100!");

    }
}
```



### i/o框架

主要是commond i/o，需要自行下载，阿帕奇

![image-20240112172012899](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112172012899.png)

![image-20240112172044416](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240112172044416.png)

## 泛型

JDK5之后的新类型

只支持引用型数据类型

泛型的通配符，但是只有一个通配符可能导致集合的元素出现一些不规范的对象，于是引入了泛型上下限的概念，可以让泛型接受某个类的子类![image-20231212135024041](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212135024041.png)

![image-20231212135105204](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212135105204.png)

下面是上下限的使用格式，规范了继承的范围

![image-20231212135646746](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212135646746.png)

下面是给Arraylist添加上下限，使dog不能成为集合的元素

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212135830054.png)

![image-20231212105303615](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212105303615.png)

### 自定义泛型类

 ![image-20231212105418165](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212105418165.png)

这是一个实现的代码，泛型

![image-20231212105759031](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212105759031.png)

### 自定义泛型方法

使方法更具有通用性

![image-20231212105957049](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212105957049.png)

### 泛型接口

  ![image-20231212134550185](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212134550185.png)

```java
public interface Data<E> {
    void add(E e);
    void delete(int id);
    void update(E e);
    E queryById(int id);
}
```



## 12.集合

### 不可变集合

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106150741734.png)



创建不可变集合

of()方法

![image-20240106155542339](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106155542339.png)

![image-20240106151132862](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106151132862.png)

### Collections集合

addall方法，利用可变参数一次添加多个元素

![image-20240105210453870](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240105210453870.png)

![image-20240105210223656](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240105210223656.png)

![image-20240105211212852](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240105211212852.png) 



集合是一种可变的容器，存储的是对象类型的容器 

![image-20231211085804115](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211085804115.png)

### Collection

单列集合接口

![image-20231211090230795](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211090230795.png)

![image-20231211090253264](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211090253264.png)

集合都是支持泛型

![image-20231211090813315](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211090813315.png)

#### collection接口的抽象方法

实现collection接口的实现类都包含下面方法

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211091432576.png)

 下面的代码中有一个补充的方法，addall 

```java
package com.itheima.d2_collection_api;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;

/**
    目标：Collection集合的常用API.
    Collection是集合的祖宗类，它的功能是全部集合都可以继承使用的，所以要学习它。
    Collection API如下:
         - public boolean add(E e)：  把给定的对象添加到当前集合中 。
         - public void clear() :清空集合中所有的元素。
         - public boolean remove(E e): 把给定的对象在当前集合中删除。
         - public boolean contains(Object obj): 判断当前集合中是否包含给定的对象。
         - public boolean isEmpty(): 判断当前集合是否为空。
         - public int size(): 返回集合中元素的个数。
         - public Object[] toArray(): 把集合中的元素，存储到数组中。
    小结：
        记住以上API。
 */
public class CollectionDemo {
    public static void main(String[] args) {
        // HashSet:添加的元素是无序，不重复，无索引。
        Collection<String> c = new ArrayList<>();
        // 1.添加元素, 添加成功返回true。
        c.add("Java");
        c.add("HTML");
        System.out.println(c.add("HTML"));
        c.add("MySQL");
        c.add("Java");
        System.out.println(c.add("黑马"));
        System.out.println(c); // [Java, HTML, HTML, MySQL, Java, 黑马]

        // 2.清空集合的元素。
        // c.clear();
        // System.out.println(c);

        // 3.判断集合是否为空 是空返回true,反之。
        // System.out.println(c.isEmpty());

        // 4.获取集合的大小。
        System.out.println(c.size());

        // 5.判断集合中是否包含某个元素。
        System.out.println(c.contains("Java"));  // true
        System.out.println(c.contains("java")); // false
        System.out.println(c.contains("黑马")); // true

        // 6.删除某个元素:如果有多个重复元素默认删除前面的第一个！
        System.out.println(c.remove("java")); // false
        System.out.println(c);
        System.out.println(c.remove("Java")); // true
        System.out.println(c);

        // 7.把集合转换成数组  [HTML, HTML, MySQL, Java, 黑马]
        Object[] arrs = c.toArray();
        System.out.println("数组：" + Arrays.toString(arrs));

        System.out.println("----------------------拓展----------------------");
        Collection<String> c1 = new ArrayList<>();
        c1.add("java1");
        c1.add("java2");
        Collection<String> c2 = new ArrayList<>();
        c2.add("赵敏");
        c2.add("殷素素");
        // addAll把c2集合的元素全部倒入到c1中去。
        c1.addAll(c2);
        System.out.println(c1);
        System.out.println(c2);
    }
}

```

#### 迭代器

#### ![image-20231211092451246](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211092451246.png)

迭代的实例，首先是创建迭代器对象，之后利用迭代器的方法进行迭代

*迭代器初始化后指针指向集合的第一个元素，next方法结束后，指向下一个位置*需要注意的事迭代器可能存在指针越界

![image-20231211092910220](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211092910220.png) 

![image-20231211093221940](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211093221940.png)

#### 集合的foreach遍历，本质就是一个迭代器

![image-20231211094153423](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211094153423.png)

#### 通过lambda表达式遍历集合

![image-20231211094442054](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211094442054.png)

![image-20231211094847100](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211094847100.png)

最终可以简化成函数引用式

![image-20231211094917203](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211094917203.png)

```java
public class CollectionDemo03 {
    public static void main(String[] args) {
        Collection<String> lists = new ArrayList<>();
        lists.add("赵敏");
        lists.add("小昭");
        lists.add("殷素素");
        lists.add("周芷若");
        System.out.println(lists);
        // [赵敏, 小昭, 殷素素, 周芷若]
        //  s
        lists.forEach(new Consumer<String>() {
            @Override
            public void accept(String s) {
                System.out.println(s);
            }
        });

//        lists.forEach(s -> {
//                System.out.println(s);
//        });

        // lists.forEach(s ->  System.out.println(s) );

        lists.forEach(System.out::println );

    }
}

```

#### *函数引用式*

在 Java 中，`System.out::println` 是一个方法引用的例子，这是 Java 8 引入的一种简洁的语法，用于引用一个方法而不是执行它。它通常用在函数式编程的上下文中，尤其是与流（streams）和 lambda 表达式结合使用时。

具体到你的例子 `lists.forEach(System.out::println);`：

- `lists` 是一个集合（比如 `List`）。
- `forEach` 是一个方法，它接受一个函数作为参数，并对集合中的每个元素执行这个函数。
- `System.out::println` 是对 `System.out.println` 方法的引用。

在这个上下文中，`System.out::println` 等同于 lambda 表达式 `(element) -> System.out.println(element)`。它会遍历 `lists` 集合中的每个元素，并对每个元素执行 `System.out.println(element)`，打印每个元素。

方法引用的一般形式是：

- `类名::静态方法名`，例如 `Math::sqrt`
- `对象引用::实例方法名`，例如 `System.out::println`
- `类名::实例方法名`，用于第一个参数会成为方法的调用者，例如 `String::length`

这种语法使得代码更简洁、更清晰，并且更易于阅读。

### List集合

![image-20231211181314044](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211181314044.png)

list的特有方法

![image-20231211181745754](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211181745754.png)









#### ArrayList

动态数组

动态扩容

集合的使用会存在空间浪费

![image-20231201160040585](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201160040585.png)

![image-20231201155646709](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201155646709.png)

#### 常用的构造方法

![image-20231201155922805](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201155922805.png)

指定特殊的方法

![image-20231201160417800](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201160417800.png)

jdk7之后，等号后面的尖括号可以不用写类型-----------**泛型**

泛型的类型只能是对象

![image-20231201160638879](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201160638879.png)

#### ArrayList中的常用方法

**指定位置添加的add返回值不是布尔类型**

![image-20231201163102347](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201163102347.png)

![image-20231201165344480](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231201165344480.png)

在集合之间中遍历删除元素，若要删除的元素有多个需要对i--

**如果是倒序遍历就不用i++**

Arraylist的四种遍历

```java
public static void main(String[] args) {
        List<String> lists = new ArrayList<>();
        lists.add("java1");
        lists.add("java2");
        lists.add("java3");

        /** （1）for循环。 */
        System.out.println("-----------------------");

        for (int i = 0; i < lists.size(); i++) {
            String ele = lists.get(i);
            System.out.println(ele);
        }


        /** （2）迭代器。 */
        System.out.println("-----------------------");
        Iterator<String> it = lists.iterator();
        while (it.hasNext()){
            String ele = it.next();
            System.out.println(ele);
        }

        /** （3）foreach */
        System.out.println("-----------------------");
        for (String ele : lists) {
            System.out.println(ele);
        }

        /** （4）JDK 1.8开始之后的Lambda表达式  */
        System.out.println("-----------------------");
        lists.forEach(s -> {
            System.out.println(s);
        });

    }
```

#### Linklist

##### 特有api

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211182646908.png)

foreach遍历list的时候没办法变遍历变删除元素，会引发并发修改错误，用Iterator遍历删除的时候可以借助迭代器对象的remove方法进行删除元素，实现变遍历边删除

![image-20231211184346218](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231211184346218.png)

如果直接使用for循环删除的时候如果从头开始遍历需要对i--，如果是从尾部遍历就可以解决这个问题

###   Set类集合

- 不重复
- 无序
- 没有索引 --------------*没有get方法* 

![image-20231212141058536](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212141058536.png)

#### HashSet

hashSet的api大多都是collection内的接口方法，常见方法参照collection的接口 

 ![image-20231212142508940](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212142508940.png)

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212142553792.png)

`public int hashCode()`----------------*返回哈希值* 

同一个对象的哈希值相同

##### hashset的底层原理

###### 1.7之前的版本

默认创建长度为16的数组，填满null

**哈希表是一种增删改查性能都挺好的数据结构**

链表的实现主要是哈希值取余相同，挂上链表

![image-20231212143136720](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212143136720.png)

###### 1.8之后的版本

 实现原理出现了红黑树，优化性能，把链表表长超过八的链表转换成红黑树，**红黑树的数值是通过哈希值的大小来比较**。其他的原理与1.7一样

#### LinkHashSet

由于用双链表记录顺序，牺牲了一定的空间，空间复杂度较高

![image-20231212144929984](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212144929984.png)

![image-20231212145011657](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212145011657.png)

#### TreeSet

![image-20231212145054377](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212145054377.png)

TreeSet的排序规则

![image-20231212145113863](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212145113863.png)

![image-20231212145134293](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212145134293.png)



##### 自定义Treeset的排序规则

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231212150221974.png)

## Map（重要）

类似字典，一个映射型的数据结构

### 概述

![image-20240105220625043](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240105220625043.png)

### 体系特点

map是一个接口



![image-20240105221252190](/Users/xiechen/Library/Application Support/typora-user-images/image-20240105221252190.png)

### Map的常用api

均有实现或重载的接口

下面这个图没有get方法，这个get方法就是python中的dict.get的用法,根据键来获得值

``` java
public Set<k> keySet()  //return all key
public Collention<V> values() //return all values
//合并集合
  map.putall()
//返回值的时候之所以不用Set集合主要是害怕值的重复导致Set直接吧重复的值给删去，所以使用Collection作为返回值
```

![image-20240105221738294](/Users/xiechen/Library/Application Support/typora-user-images/image-20240105221738294.png)

### 遍历方式

![image-20240105222842274](/Users/xiechen/Library/Application Support/typora-user-images/image-20240105222842274.png)

**直接通过键来遍历**

```java

/**
    目标：Map集合的遍历方式一：键找值

    Map集合的遍历方式有：3种。
        （1）“键找值”的方式遍历：先获取Map集合全部的键，再根据遍历键找值。
        （2）“键值对”的方式遍历：难度较大。
        （3）JDK 1.8开始之后的新技术：Lambda表达式。（暂时了解）

    a.“键找值”的方式遍历Map集合。
        1.先获取Map集合的全部键的Set集合。
        2.遍历键的Set集合，然后通过键找值。
    小结：
        代码简单，需要记住!

 */
public class MapDemo01 {
    public static void main(String[] args) {
        Map<String , Integer> maps = new HashMap<>();
        // 1.添加元素: 无序，不重复，无索引。
        maps.put("娃娃",30);
        maps.put("iphoneX",100);
        maps.put("huawei",1000);
        maps.put("生活用品",10);
        maps.put("手表",10);
        System.out.println(maps);
        // maps = {huawei=1000, 手表=10, 生活用品=10, iphoneX=100, 娃娃=30}

        // 1、键找值：第一步：先拿到集合的全部键。
        Set<String> keys = maps.keySet();
        // 2、第二步：遍历每个键，根据键提取值
        for (String key : keys) {
            int value = maps.get(key);
            System.out.println(key + "===>" + value);
        }

    }
}

```



**Lambda表达式遍历**

```java
import java.util.HashMap;
import java.util.Map;
import java.util.function.BiConsumer;

/**
    目标：Map集合的遍历方式。

    Map集合的遍历方式有：3种。
        （1）“键找值”的方式遍历：先获取Map集合全部的键，再根据键找值。
        （2）“键值对”的方式遍历：难度较大。
        （3）JDK 1.8开始之后的新技术：Lambda表达式。

    c.JDK 1.8开始之后的新技术：Lambda表达式。（暂时了解）
 */
public class MapDemo03 {
    public static void main(String[] args) {
        Map<String , Integer> maps = new HashMap<>();
        // 1.添加元素: 无序，不重复，无索引。
        maps.put("娃娃",30);
        maps.put("iphoneX",100);//  Map集合后面重复的键对应的元素会覆盖前面重复的整个元素！
        maps.put("huawei",1000);
        maps.put("生活用品",10);
        maps.put("手表",10);
        System.out.println(maps);

        //  maps = {huawei=1000, 手表=10, 生活用品=10, iphoneX=100, 娃娃=30}

//        maps.forEach(new BiConsumer<String, Integer>() {
//            @Override
//            public void accept(String key, Integer value) {
//                System.out.println(key + "--->" + value);
//            }
//        });

        maps.forEach((k, v) -> {
                System.out.println(k + "--->" + v);
        });

    }
}
```

最后终极的代码就是最后一行的这个

```java
maps.forEach((key,value) ->{
	 pass;//需要遍历的操作
});
```

```java
import java.util.*;
 
public class Test{
     public static void main(String[] args) {
      Map<String, String> map = new HashMap<String, String>();
      map.put("1", "value1");
      map.put("2", "value2");
      map.put("3", "value3");
      
      //第一种：普遍使用，二次取值
      System.out.println("通过Map.keySet遍历key和value：");
      for (String key : map.keySet()) {
       System.out.println("key= "+ key + " and value= " + map.get(key));
      }
      
      //第二种
      System.out.println("通过Map.entrySet使用iterator遍历key和value：");
      Iterator<Map.Entry<String, String>> it = map.entrySet().iterator();
      while (it.hasNext()) {
       Map.Entry<String, String> entry = it.next();
       System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
      }
      
      //第三种：推荐，尤其是容量大时
      System.out.println("通过Map.entrySet遍历key和value");
      for (Map.Entry<String, String> entry : map.entrySet()) {
       System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
      }
    
      //第四种
      System.out.println("通过Map.values()遍历所有的value，但不能遍历key");
      for (String v : map.values()) {
       System.out.println("value= " + v);
      }
     }
}
```



## 日期类

### Date类

![image-20231206203944782](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206203944782.png)

![image-20231206205225553](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206205225553.png)

### SimpleDateFormat类

![image-20231206210300571](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206210300571.png)

格式化的模型

![image-20231206210354983](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206210354983.png)

#### 解析字符串时间

![image-20231206211419484](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206211419484.png)

```java
public static void main(String[] args) throws ParseException {
        // 目标: 学会使用SimpleDateFormat解析字符串时间成为日期对象。
        // 有一个时间 2021年08月06日 11:11:11 往后 2天 14小时 49分 06秒后的时间是多少。
        // 1、把字符串时间拿到程序中来
        String dateStr = "2021年08月06日 11:11:11";

        // 2、把字符串时间解析成日期对象（本节的重点）:形式必须与被解析时间的形式完全一样，否则运行时解析报错！
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
        Date d = sdf.parse(dateStr);

        // 3、往后走2天 14小时 49分 06秒
        long time = d.getTime() + (2L*24*60*60 + 14*60*60 + 49*60 + 6) * 1000;

        // 4、格式化这个时间毫秒值就是结果
        System.out.println(sdf.format(time));
```

![image-20231206212700559](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206212700559.png)

### Calendar

Calendar是一个抽象类，不能直接创建对象，需要通过对应的getInstance()方法来获取对象

![image-20231206212721032](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206212721032.png)

常用方法



![image-20231206212854745](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206212854745.png)

```java
public static void main(String[] args) {
        // 1、拿到系统此刻日历对象
        Calendar cal = Calendar.getInstance();
        System.out.println(cal);

        // 2、获取日历的信息:public int get(int field)：取日期中的某个字段信息。
        int year = cal.get(Calendar.YEAR);
        System.out.println(year);

        int mm = cal.get(Calendar.MONTH) + 1;
        System.out.println(mm);

        int days = cal.get(Calendar.DAY_OF_YEAR) ;
        System.out.println(days);

        // 3、public void set(int field,int value)：修改日历的某个字段信息。
        // cal.set(Calendar.HOUR , 12);
        // System.out.println(cal);

        // 4.public void add(int field,int amount)：为某个字段增加/减少指定的值
        // 请问64天后是什么时间
        cal.add(Calendar.DAY_OF_YEAR , 64);
        cal.add(Calendar.MINUTE , 59);

        //  5.public final Date getTime(): 拿到此刻日期对象。
        Date d = cal.getTime();
        System.out.println(d);

        //  6.public long getTimeInMillis(): 拿到此刻时间毫秒值
        long time = cal.getTimeInMillis();
        System.out.println(time);

```

### JDK8之后的日期API

了解，具体开发具体查询

![image-20231206213520964](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206213520964.png)

LocalDate

```java
 public static void main(String[] args) {
        // 1、获取本地日期对象。
        LocalDate nowDate = LocalDate.now();
        System.out.println("今天的日期：" + nowDate);//今天的日期：

        int year = nowDate.getYear();
        System.out.println("year：" + year);


        int month = nowDate.getMonthValue();
        System.out.println("month：" + month);

        int day = nowDate.getDayOfMonth();
        System.out.println("day：" + day);

        //当年的第几天
        int dayOfYear = nowDate.getDayOfYear();
        System.out.println("dayOfYear：" + dayOfYear);

        //星期
        System.out.println(nowDate.getDayOfWeek());
        System.out.println(nowDate.getDayOfWeek().getValue());

        //月份
        System.out.println(nowDate.getMonth());
        System.out.println(nowDate.getMonth().getValue());

        System.out.println("------------------------");
        LocalDate bt = LocalDate.of(1991, 11, 11);
        System.out.println(bt);//直接传入对应的年月日
        System.out.println(LocalDate.of(1991, Month.NOVEMBER, 11));//相对上面只是把月换成了枚举
    }
```

![image-20231206214108100](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206214108100.png)

![image-20231206214119480](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206214119480.png)

![image-20231206214346810](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231206214346810.png)

## 正则表达式

具体参见python中

java中的正则表达式的方法存放在String类当中

![image-20231208092851170](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208092851170.png)

### 切割，替换

![image-20231208094935166](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208094935166.png)

```java
//切割字符串
public static void main(String[] args) {
        String names = "小路dhdfhdf342蓉儿43fdffdfbjdfaf小何";

        String[] arrs = names.split("\\w+");
        for (int i = 0; i < arrs.length; i++) {
            System.out.println(arrs[i]);
        }

        String names2 = names.replaceAll("\\w+", "  ");
        System.out.println(names2);
    }
```

### **实例代码----*在爬去信息中的应用***



![image-20231208100110696](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208100110696.png)

## 13.Arrays

用于操作数组

### 常用方法

基本上是静态方法



![image-20231208164107892](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208164107892.png)

二分查找的关键还是已经排好序的数组

二分查找的不存在返回值是应当插入index+1的负数

### 构造器排序

可以指定正序，或者逆序，以及可以指定对象里面的对应元素进行排序

![image-20231208171655831](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208171655831.png)

下面例子是一个对一个学生类对象里面的学生年龄进行排序

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208171750852.png)

例子二，使用比较器按照字符串长短进行排序

```java
import java.util.Arrays;
import java.util.Comparator;

public class Main {
    public static void main(String[] args) {
        // 创建一个包含字符串的数组
        String[] names = {"Alice", "Bob", "Charlie", "David"};

        // 使用默认的自然排序对数组进行排序
        Arrays.sort(names);
        System.out.println("默认排序后的数组：");
        System.out.println(Arrays.toString(names));

        // 创建一个自定义的Comparator对象，按字符串长度进行降序排序
        Comparator<String> lengthComparator = new Comparator<String>() {
            @Override
            public int compare(String s1, String s2) {
                return Integer.compare(s2.length(), s1.length()); //大于返回1
              																										//小于返回-1，等于返回0
            }
        };

        // 使用自定义的Comparator对象进行排序
        Arrays.sort(names, lengthComparator);
        System.out.println("按字符串长度降序排序后的数组：");
        System.out.println(Arrays.toString(names));
    }
}

```

## 14.Lambda表达式

简化匿名内部类

![image-20231208174113730](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208174113730.png)

java中的lambda只能实现含有一个抽象方法的接口---------*函数式接口*，这个有对应的修饰符

![image-20231208192309869](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208192309869.png)

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208192602563.png)

![image-20231208192620880](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208192620880.png)

lambda简化的实例

![image-20231208193001274](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208193001274.png)

降序的lambda简化

![image-20231208193243784](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208193243784.png)

省略规则

![image-20231208193456373](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231208193456373.png)

## 可变参数

可变参数对内就是数组

![image-20240105205344423](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240105205344423.png)

## 15.Stream（重要）

通过获取集合的流，来不断过滤元素，所以称为流，因此要使用数据结构的Stream流必须先获取他的Stream

几种数据类型获流的方法

![image-20240106161109074](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106161109074.png)

### 常用api

![image-20240106162016126](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106162016126.png)

常见的还有

`startWith()`

![image-20240106162035264](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106162035264.png)当操作完Stream之后需要再用集合把流收集起来

![image-20240106165625946](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106165625946.png)

![image-20240106165708734](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106165708734.png)

## 16.异常

![image-20240106191412221](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106191412221.png)

![image-20240106192754680](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106192754680.png)

Java 根据各个类库也定义了一些其他的异常，下面的表中列出了 Java 的非检查性异常(运行时异常)。



| **异常**                        |                                                     **描述** |
| :------------------------------ | -----------------------------------------------------------: |
| ArithmeticException             | 当出现异常的运算条件时，抛出此异常。例如，一个整数"除以零"时，抛出此类的一个实例。 |
| ArrayIndexOutOfBoundsException  | 用非法索引访问数组时抛出的异常。如果索引为负或大于等于数组大小，则该索引为非法索引。 |
| ArrayStoreException             |         试图将错误类型的对象存储到一个对象数组时抛出的异常。 |
| ClassCastException              |         当试图将对象强制转换为不是实例的子类时，抛出该异常。 |
| IllegalArgumentException        |         抛出的异常表明向方法传递了一个不合法或不正确的参数。 |
| IllegalMonitorStateException    | 抛出的异常表明某一线程已经试图等待对象的监视器，或者试图通知其他正在等待对象的监视器而本身没有指定监视器的线程。 |
| IllegalStateException           | 在非法或不适当的时间调用方法时产生的信号。换句话说，即 Java 环境或 Java 应用程序没有处于请求操作所要求的适当状态下。 |
| IllegalThreadStateException     |           线程没有处于请求操作所要求的适当状态时抛出的异常。 |
| IndexOutOfBoundsException       | 指示某排序索引（例如对数组、字符串或向量的排序）超出范围时抛出。 |
| NegativeArraySizeException      |           如果应用程序试图创建大小为负的数组，则抛出该异常。 |
| NullPointerException            |     当应用程序试图在需要对象的地方使用 `null` 时，抛出该异常 |
| NumberFormatException           | 当应用程序试图将字符串转换成一种数值类型，但该字符串不能转换为适当格式时，抛出该异常。 |
| SecurityException               |                   由安全管理器抛出的异常，指示存在安全侵犯。 |
| StringIndexOutOfBoundsException | 此异常由 `String` 方法抛出，指示索引或者为负，或者超出字符串的大小。 |
| UnsupportedOperationException   |                           当不支持请求的操作时，抛出该异常。 |

下面的表中列出了 Java 定义在 java.lang 包中的检查性异常类(编译时异常)。

编译时异常就是在编写代码的时候就需要处理的错误



| **异常**                   | **描述**                                                     |
| :------------------------- | :----------------------------------------------------------- |
| ClassNotFoundException     | 应用程序试图加载类时，找不到相应的类，抛出该异常。           |
| CloneNotSupportedException | 当调用 `Object` 类中的 `clone` 方法克隆对象，但该对象的类无法实现 `Cloneable` 接口时，抛出该异常。 |
| IllegalAccessException     | 拒绝访问一个类的时候，抛出该异常。                           |
| InstantiationException     | 当试图使用 `Class` 类中的 `newInstance` 方法创建一个类的实例，而指定的类对象因为是一个接口或是一个抽象类而无法实例化时，抛出该异常。 |
| InterruptedException       | 一个线程被另一个线程中断，抛出该异常。                       |
| NoSuchFieldException       | 请求的变量不存在                                             |
| NoSuchMethodException      | 请求的方法不存在                                             |

### 异常的处理机制

try-catch-finaly放在io那边写了，具体参考那边

异常的默认机制并不好，会直接杀死程序

![image-20240106195814275](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106195814275.png)

![image-20240106200256122](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106200256122.png)

#### 自行处理编译时异常的方法

idea中alt加回车可以自动出现解决代码 

##### throws

虽然可以抛出多个异常，但是最后只能抛出第一个出现的异常

`throws Exception`可以直接把所有的异常都给抛出，而不需要一个一个的列出异常

![image-20240106200539351](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106200539351.png)

##### Try-catch

![image-20240106201511913](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106201511913.png)

![image-20240106201431854](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106201431854.png)

**企业级写法**，直接拦截一切异常

![image-20240106201539760](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106201539760.png)

##### 不断抛到上层解决异常



```java
public class ExceptionDemo03 {
    public static void main(String[] args) {
        System.out.println("程序开始。。。。");
        try {
            parseTime("2011-11-11 11:11:11");
            System.out.println("功能操作成功~~~");
        } catch (Exception e) {
            e.printStackTrace();
            System.out.println("功能操作失败~~~");
        }
        System.out.println("程序结束。。。。");
    }

    public static void parseTime(String date) throws Exception {
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy、MM-dd HH:mm:ss");
        Date d = sdf.parse(date);
        System.out.println(d);

        InputStream is = new FileInputStream("D:/meinv.jpg");
    }
```

### 运行时异常处理

数组越界这样的异常，可以不处理这样的异常，因为编译时可以通过

案例

下面这个案例可以重复循环知道合法输入

```java
import java.util.Scanner;

/**
    需求：需要输入一个合法的价格为止 要求价格大于 0
 */
public class Test2 {
    public static void main(String[] args) {
        Scanner sc  = new Scanner(System.in);
        while (true) {
            try {
                System.out.println("请您输入合法的价格：");
                String priceStr = sc.nextLine();
                // 转换成double类型的价格
                double price = Double.valueOf(priceStr);

                // 判断价格是否大于 0
                if(price > 0) {
                    System.out.println("定价：" + price);
                    break;
                }else {
                    System.out.println("价格必须是正数~~~");
                }
            } catch (Exception e) {
                System.out.println("用户输入的数据有毛病，请您输入合法的数值，建议为正数~~");
            }
        }
    }
}
```

### 自定义异常

写一个继承与Exception

#### 编译时异常

![image-20240106203706801](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240106203706801.png)

`throws` 和 `throw` 都与异常处理有关，但它们用于不同的情况，并有不同的作用：

1. **throws：** 

   - `throws` 关键字用于方法签名中，表示该方法可能会抛出某种类型的异常。例如：
   
     ```java
     public void someMethod() throws IOException {
         // 方法实现
     }
     ```

   - 当在方法中使用了可能会抛出编译时异常的代码时，编译器要求在方法签名中使用 `throws` 来声明这些异常。这告诉调用者这个方法可能会抛出异常，需要在调用该方法时进行异常处理（使用 `try-catch` 或者将异常继续传播）。

2. **throw：**

   - `throw` 关键字用于在方法内部手动抛出异常。可以使用 `throw` 来抛出任何类型的异常，包括自定义异常。例如：
   
     ```java
     public void someMethod() {
         if (someCondition) {
             throw new SomeException("Something went wrong");
         }
     }
     ```

   - 这允许程序员在特定条件下主动引发异常，而不是等待自然发生的异常。这对于在代码中明确定义异常情况时非常有用。

总结区别：
- `throws` 用于声明方法可能抛出的异常类型，是方法的一部分，用于编译时检查。
- `throw` 用于在方法内部手动抛出异常，可以用于任何时候，是具体代码的一部分。

需要注意的是，`throws` 常用于编译时异常的处理，而 `throw` 常用于运行时异常的手动触发。

下面是自定义编译时异常的类，继承的是Exception

```java
package com.itheima.d9_exception_custom;

/**
    自定义的编译时异常
      1、继承Exception
      2、重写构造器
 */
public class  ItheimaAgeIlleagalException extends Exception{
    public ItheimaAgeIlleagalException() {
    }

    public ItheimaAgeIlleagalException(String message) {
        super(message);
    }
}
```

下面是自定义运行时异常，继承的类是RuntimeException

```java
package com.itheima.d9_exception_custom;

/**
    自定义的编译时异常
      1、继承RuntimeException
      2、重写构造器
 */
public class ItheimaAgeIlleagalRuntimeException extends RuntimeException{
    public ItheimaAgeIlleagalRuntimeException() {
    }

    public ItheimaAgeIlleagalRuntimeException(String message) {
        super(message);
    }
}
```

```java
package com.itheima.d9_exception_custom;
/**
    目标:自定义异常(了解)

    引入:Java已经为开发中可能出现的异常都设计了一个类来代表.
        但是实际开发中,异常可能有无数种情况,Java无法为
        这个世界上所有的异常都定义一个代表类。
        假如一个企业如果想为自己认为的某种业务问题定义成一个异常
        就需要自己来自定义异常类.

    需求：认为年龄小于0岁，大于200岁就是一个异常。

    自定义异常:
        自定义编译时异常.
            a.定义一个异常类继承Exception.
            b.重写构造器。
            c.在出现异常的地方用throw new 自定义对象抛出!
            编译时异常是编译阶段就报错，提醒更加强烈，一定需要处理！！

        自定义运行时异常.
            a.定义一个异常类继承RuntimeException.
            b.重写构造器。
            c.在出现异常的地方用throw new 自定义对象抛出!
            提醒不强烈，编译阶段不报错！！运行时才可能出现！！

 */
public class ExceptionDemo {
    public static void main(String[] args) {
//        try {
//            checkAge(-34);
//        } catch (ItheimaAgeIlleagalException e) {
//            e.printStackTrace();
//        }

        try {
            checkAge2(-23);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void checkAge2(int age)//运行时异常不用thorw  {
        if(age < 0 || age > 200){
            // 抛出去一个异常对象给调用者
            // throw ：在方法内部直接创建一个异常对象，并从此点抛出
            // throws : 用在方法申明上的，抛出方法内部的异常
            throw new ItheimaAgeIlleagalRuntimeException(age + " is illeagal!");
        }else {
            System.out.println("年龄合法：推荐商品给其购买~~");
        }
    }

    public static void checkAge(int age) throws ItheimaAgeIlleagalException//编译时异常需要再抛出方法异常  {
        if(age < 0 || age > 200){
            // 抛出去一个异常对象给调用者
            // throw ：在方法内部直接创建一个异常对象，并从此点抛出
            // throws : 用在方法申明上的，抛出方法内部的异常
            throw new ItheimaAgeIlleagalException(age + " is illeagal!");
        }else {
            System.out.println("年龄合法：推荐商品给其购买~~");
        }
    }
}
```

## Logback日志框架

记录系统运行的信息，存储到控制台，数据库，文本文件当中,Logback基于slf4j设计

需要导入对应的日志包

![image-20240107195043841](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107195043841.png)

![image-20240107193120454](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107193120454.png)

![image-20240107193559174](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107193559174.png)

![image-20240107193610998](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107193610998.png)

### 快速入门

![image-20240107194730537](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107194730537.png)

获取日志对象![image-20240107194800137](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107194800137.png)

xml的文件配置，可以配置文件与控制台



![image-20240107200212601](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107200212601.png)

日志文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!--
        CONSOLE ：表示当前的日志信息是可以输出到控制台的。
    -->
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <!--输出流对象 默认 System.out 改为 System.err-->
        <target>System.out</target>
        <encoder>
            <!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度
                %msg：日志消息，%n是换行符-->
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%-5level]  %c [%thread] : %msg%n</pattern>
        </encoder>
    </appender>

    <!-- File是输出的方向通向文件的 -->
    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!--日志输出路径-->
        <file>C:/code/itheima-data.log</file>
        <!--指定日志文件拆分和压缩规则-->
        <rollingPolicy
                class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <!--通过指定压缩文件名称，来确定分割文件方式-->
            <fileNamePattern>C:/code/itheima-data2-%d{yyyy-MMdd}.log%i.gz</fileNamePattern>
            <!--文件拆分大小，不大于1MB-->
            <maxFileSize>1MB</maxFileSize>
        </rollingPolicy>
    </appender>

    <!--

    level:用来设置打印级别，大小写无关：TRACE, DEBUG, INFO, WARN, ERROR, ALL 和 OFF
   ， 默认debug
    <root>可以包含零个或多个<appender-ref>元素，标识这个输出位置将会被本日志级别控制。
    -->
    <root level="ALL">
      <!--- 如果这里不配置appender-ref 就不会记录日志--->
        <appender-ref ref="CONSOLE"/>
        <appender-ref ref="FILE" />
    </root>
</configuration>
```

##### ![image-20240107201121876](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107201121876.png)

### 日志级别设置

日志级别用于控制需要输出的信息类别

![image-20240107201320397](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107201320397.png)

![image-20240107201606377](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240107201606377.png)

## 多线程

### 三种创建线程的方法

![image-20240118195510556](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118195510556.png)

第一种直接通过继承Thread类并且重写run方法

```java
package mycode;

public class threadCreatMethod {
    public static void main(String[] args) {
        Thread demo1 = new myThread();
        //这里直接调用run的话会被当成普通的方法，而不是多线程
        demo1.start();
    }
}
class myThread extends Thread {
    @Override
    public void run(){
        System.out.println("小谦谦成功了吗");
    }
}
```

第二种方法

通过Runnable接口创建多线程

比较不好的是需要执行返回结果的时候runnable没办法返回值

```java
package mycode;

/**
 *  实现runnable接口
* */
public class threadCreatMethod2 {
    public static void main(String[] args) {
        byRunnable demo1 = new byRunnable();
        Thread threadDemo2 = new Thread(demo1);

        threadDemo2.start();
    }
}
class byRunnable implements Runnable{
    @Override
    public void run(){
        System.out.println("通过runnable创建对象");
    }
}
```

![image-20240118201055684](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118201055684.png)

第三种Callable实现

![image-20240118201923313](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118201923313.png)

![image-20240118203653909](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118203653909.png)

```java
package com.itheima.d1_create;

import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
   目标：学会线程的创建方式三：实现Callable接口，结合FutureTask完成。
 */
public class ThreadDemo3 {
    public static void main(String[] args) {
        // 3、创建Callable任务对象
        Callable<String> call = new MyCallable(100);
        // 4、把Callable任务对象 交给 FutureTask 对象
        //  FutureTask对象的作用1： 是Runnable的对象（实现了Runnable接口），可以交给Thread了
        //  FutureTask对象的作用2： 可以在线程执行完毕之后通过调用其get方法得到线程执行完成的结果
        FutureTask<String> f1 = new FutureTask<>(call);
        // 5、交给线程处理
        Thread t1 = new Thread(f1);
        // 6、启动线程
        t1.start();


        Callable<String> call2 = new MyCallable(200);
        FutureTask<String> f2 = new FutureTask<>(call2);
        Thread t2 = new Thread(f2);
        t2.start();

        try {
            // 如果f1任务没有执行完毕，这里的代码会等待，直到线程1跑完才提取结果。
            String rs1 = f1.get();
            System.out.println("第一个结果：" + rs1);
        } catch (Exception e) {
            e.printStackTrace();
        }

        try {
            // 如果f2任务没有执行完毕，这里的代码会等待，直到线程2跑完才提取结果。
            String rs2 = f2.get();
            System.out.println("第二个结果：" + rs2);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

/**
    1、定义一个任务类 实现Callable接口  应该申明线程任务执行完毕后的结果的数据类型
 */
class MyCallable implements Callable<String>{
    private int n;
    public MyCallable(int n) {
        this.n = n;
    }

    /**
       2、重写call方法（任务方法）
     */
    @Override
    public String call() throws Exception {
        int sum = 0;
        for (int i = 1; i <= n ; i++) {
            sum += i;
        }
        return "子线程执行的结果是：" + sum;
    }
}
```

![image-20240118203727249](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118203727249.png)

### 线程的常用api

![image-20240118203812325](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118203812325.png)

![image-20240118203923815](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118203923815.png)

![image-20240118203933174](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118203933174.png)

void static sleep

线程的休眠，以毫秒为单位让程序休眠

### Thread的构造器

![image-20240118204509073](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240118204509073.png)

### 线程安全

多个线程同时操作同一个共享资源的时候可能会出现业务安全问题，称为线程安全问题

![image-20240120115420304](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120115420304.png)

线程出现的原因

![image-20240120115509774](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120115509774.png)

解决线程安全方法------给线程加锁

![image-20240120120643482](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120120643482.png)

#### 同步代码块

把核心代码放入synchronized语句中

![image-20240120120725955](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120120725955.png)



```java
public void drawMoney(double money) {
        // 1、拿到是谁来取钱
        String name = Thread.currentThread().getName();
        // 同步代码块
        // 小明 小红
        // this == acc 共享账户
        synchronized (this) {
            // 2、判断余额是否足够
            if(this.money >= money){
                // 钱够了
                System.out.println(name+"来取钱，吐出：" + money);
                // 更新余额
                this.money -= money;
                System.out.println(name+"取钱后，余额剩余：" + this.money);
            }else{
                // 3、余额不足
                System.out.println(name+"来取钱，余额不足！");
            }
        }
    }
}
```

```java
    // 100个线程人
    public static void run(){
synchronized (Account.class){//静态方法用类名作为锁

        }
    }
```

![image-20240120121440077](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120121440077.png)

#### 同步方法

![image-20240120121602183](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120121602183.png)

![image-20240120121611340](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120121611340.png)

```java
public synchronized void drawMoney(double money) {
        // 1、拿到是谁来取钱
        String name = Thread.currentThread().getName();
        // 2、判断余额是否足够
        // 小明  小红
        if(this.money >= money){
            // 钱够了
            System.out.println(name+"来取钱，吐出：" + money);
            // 更新余额
            this.money -= money;
            System.out.println(name+"取钱后，余额剩余：" + this.money);
        }else{
            // 3、余额不足
            System.out.println(name+"来取钱，余额不足！");
        }
    }
}
```

![image-20240120121722751](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120121722751.png)

#### lock锁（了解）

![image-20240120121908562](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120121908562.png)

### 线程池

![image-20240120122031093](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120122031093.png)

实现原理，线程队列

![image-20240120122054395](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120122054395.png)

实现线程池的一些api，主要掌握第一种方式

![image-20240120122251911](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120122251911.png)

ThreadpoolExecutor的常见构造器

![image-20240120122347916](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120122347916.png)

![image-20240120122808645](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120122808645.png)

#### 运用线程池创建Runnable任务

![image-20240120122951764](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120122951764.png)

拒绝任务的策略

![image-20240120124530165](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120124530165.png)

Executors得到线程池对象的常用方法

![image-20240120124902999](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120124902999.png)

以FixdThreadPool为例

```java
ExecutorService pool = Executors.newFixedThreadPool(3);
//最后的创建对象底层的源代码就是通过ThreadPoolExecutor制定对应的线程和最大线程数
```

Executors可能存在的问题

![image-20240120125326380](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120125326380.png)

![image-20240120125426113](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120125426113.png)

### 多线程实例

#### 计时器

![image-20240120125721173](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120125721173.png)

Timer是单线程，一般是使用方式二的线程池

```java
package com.itheima.d9_timer;

import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;

/**
    目标：Timer定时器的使用和了解。
 */
public class TimerDemo1 {
    public static void main(String[] args) {
        // 1、创建Timer定时器
        Timer timer = new Timer();  // 定时器本身就是一个单线程。
        // 2、调用方法，处理定时任务
        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "执行AAA~~~" + new Date());
//                try {
//                    Thread.sleep(5000);
//                } catch (InterruptedException e) {
//                    e.printStackTrace();
//                }
            }
        }, 0, 2000);

        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "执行BB~~~"+ new Date());
                System.out.println(10/0);
            }
        }, 0, 2000);

        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "执行CCC~~~"+ new Date());
            }
        }, 0, 3000);
    }
}
```

![image-20240120131308618](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120131308618.png)

ScheduledExecutorService

![image-20240120131721309](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120131721309.png)

```java
package com.itheima.d9_timer;

import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;


public class TimerDemo2 {
    public static void main(String[] args) {
        // 1、创建ScheduledExecutorService线程池，做定时器
        ScheduledExecutorService pool = Executors.newScheduledThreadPool(3);

        // 2、开启定时任务
        pool.scheduleAtFixedRate(new TimerTask() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "执行输出：AAA  ==》 " + new Date());
                try {
                    Thread.sleep(100000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }, 0, 2, TimeUnit.SECONDS);


        pool.scheduleAtFixedRate(new TimerTask() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "执行输出：BBB  ==》 " + new Date());
                System.out.println(10 / 0);
            }
        }, 0, 2, TimeUnit.SECONDS);


        pool.scheduleAtFixedRate(new TimerTask() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "执行输出：CCC  ==》 " + new Date());
            }
        }, 0, 2, TimeUnit.SECONDS);

    }
}
```

线程的集中状态

![image-20240120132754073](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120132754073.png)

![image-20240120132803254](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120132803254.png)

![image-20240120132851094](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120132851094.png)

## 网络编程

### 网络简要回顾



网络端口



![image-20240122160700701](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122160700701.png)

![image-20240120133133772](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120133133772.png)

![image-20240120133508440](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120133508440.png)

![image-20240120133615858](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120133615858.png)

![image-20240120133637220](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120133637220.png)

ipv6

![image-20240120133906933](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120133906933.png)

ipv6简要写法

![image-20240120134120975](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120134120975.png)

![image-20240120172914180](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120172914180.png)

![image-20240120173442171](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120173442171.png)

### InetAddress

![image-20240120173840557](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240120173840557.png)

```java
package InetaddressCode;

import java.net.*;

public class InetAddressAPIDemo {
    public static void main(String[] args) throws UnknownHostException {
        //获取当前ip的对象（获取这台电脑）
        InetAddress localHost = InetAddress.getLocalHost();

        //通过这台电脑的对象获得这个电脑的名字
         String localName = localHost.getHostName();

        System.out.println(localName);

        //获取这台电脑的ip
        String ip = localHost.getHostAddress();

        System.out.println(ip);


    }
}
```

### UDP通信

![image-20240122161531657](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122161531657.png)

![image-20240122164939166](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122164939166.png)

发送端

```java
package InetaddressCode.SendMessageDemo;

import java.net.*;

public class UDPSendMessage {
    /*
    *1.创建DatagramSocket对象
    * 2.绑定端口
    * 3.打包数据
    * 4.发送数据
    * 5.断开链接
    * */

    public static void main(String[] args)throws Exception {
        DatagramSocket sendSocket = new DatagramSocket();

        byte[] messageArray = "This is xielongjie".getBytes();

        InetAddress localHost = InetAddress.getLocalHost();


        int port = 60000;

        DatagramPacket sendPacket = new DatagramPacket(messageArray,messageArray.length,localHost,port);

        sendSocket.send(sendPacket);

        Thread.sleep(3000);

        sendSocket.close();
    }
}
```

接收端

```java
package InetaddressCode.SendMessageDemo;

import java.net.DatagramPacket;
import java.net.DatagramSocket;

public class UDPGetMessage {
    public static void main(String[] args)throws Exception {
        DatagramSocket getMessageSocket = new DatagramSocket(60000);
        byte[] getMessageArray = new byte[2048];

        DatagramPacket getMessagePacket = new 			DatagramPacket(getMessageArray,getMessageArray.length);
        getMessageSocket.receive(getMessagePacket);

        //解析数据包
        byte[] data = getMessagePacket.getData();


        System.out.println("接受到了这样的消息:"+new String(data,0,getMessagePacket.getLength()));

        getMessageSocket.close();
    }
}
```

#### 三种通信

三种通信主要区别是设置好发送Packet的ip

![image-20240122173700534](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122173700534.png)

![image-20240122173750371](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122173750371.png)

### TCP通信

建立好链接之后在数据包里面就不需要在制定ip与host了，因为已经建立连接，三次握手

![image-20240122174242563](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122174242563.png)

客户端操作

![image-20240122174335284](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122174335284.png)

服务器操作

![image-20240122174410649](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122174410649.png)

发送端代码![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122174603760.png)

接收端代码

![image-20240122174851410](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122174851410.png)

### 综合练习

![image-20240122184334151](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122184334151.png)

![image-20240122184345633](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122184345633.png)

![image-20240122184402787](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122184402787.png)

![image-20240122184434137](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240122184434137.png)

## Junit测试

![image-20240123155607081](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123155607081.png)

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123160936344.png)

```java
public String loginName(String loginName , String passWord){
    if("admin".equals(loginName) && "123456".equals(passWord)){
        return "登录成功";
    }else {
        return "用户名或者密码有问题";
    }
}
```

测试类的代码

```java
@Test
public void testLoginName(){
    UserService userService = new UserService();
    String rs = userService.loginName("admin","123456");

    // 进行预期结果的正确性测试：断言
    //message :断言的结果 expected :实际上的结果
    Assert.assertEquals("您的登录业务可能出现问题", "登录成功", rs );

}
```

## 反射

![image-20240123161620790](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123161620790.png)

拿去Class对象的方法

```java
package MyCode;

public class Test {

    public static void main(String[] args) throws ClassNotFoundException {
        //方法一通过forName方法
      	//后面的forName的参数是类的全类名
      
        Class clazz = Class.forName("MyCode.Student");
        System.out.println(clazz);

        //第二种直接通过对象.getclass方法

        Student xie = new Student(16,"xielongjie","190");
        Class clazz2 = xie.getClass();
        System.out.println(clazz2);

        //第三种通过类名.class获取
        Class clazz3 = Student.class;
        System.out.println(clazz3);
    }
}
```

输出结果

![image-20240123162855179](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123162855179.png)

### 通过Class对象获取构造器对象

![image-20240123162917802](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123162917802.png)

![image-20240123163050077](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123163050077.png)

代码实例

```java
package MyCode;

import java.lang.module.Configuration;
import java.lang.reflect.Constructor;

public class getConStructorTest {
    public static void main(String[] args) {
        //先拿去类的Class对象
        Class clazz = Student.class;

        //提取构造器对象
        Constructor[] constructors = clazz.getConstructors(); //获取全部public的构造器对象
        for(Constructor demo : constructors){
            System.out.println(demo.getName());
           System.out.println(demo.getModifiers());
        }

        //提取一个构造器就是getConstructor
        //获取全部构造器对象就需要getDeclaredConstructors,同样，单个的话就是去掉s返回单个对象


    }
}
```

输出

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123163749146.png)

获取有指定构造的构造器

```java
Constructor par2Con = clazz.getConstructor(int.class,String.class,String.class);
System.out.println(par2Con.getParameterCount());
```

输出

![image-20240123164119249](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123164119249.png)

反射中的暴力反射可以破坏封装性

![image-20240123164544500](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123164544500.png)

cons就是一个私有的构造器对象，学生累可以调用cons的newInstance创建一个新的学生类对象

```java
Student newStudent = (Student) par2Con.newInstance(16,"xielongjiexiaohao","18");
System.out.println(newStudent.getName());
```

输出

![image-20240123164806437](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123164806437.png)

通过反射获取成员变量

获取的步骤与方法，与获取构造器对象的方法类似

![image-20240123165113906](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123165113906.png)

通过成员变量对象对成员变量进行取值赋值

![image-20240123165843876](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123165843876.png)

```java
public void setField() throws Exception {
    // a.反射第一步，获取类对象
    Class c = Student.class;
    // b.提取某个成员变量
    Field ageF = c.getDeclaredField("age");

    ageF.setAccessible(true); // 暴力打开权限

    // c.赋值
    Student s = new Student();
    ageF.set(s , 18);  // s.setAge(18);
    System.out.println(s);

    // d、取值
    int age = (int) ageF.get(s);
    System.out.println(age);
 
```

获得特定的成员变量

```java
 public void getDeclaredField() throws Exception {
        // a.定位Class对象
        Class c = Student.class;
        // b.根据名称定位某个成员变量，getType获取数据类型
        Field f = c.getDeclaredField("age");
        System.out.println(f.getName() +"===>" + f.getType());
    }

}
```

### 获取方法的对象

获得特定的话可以通过方法的名字+形参一起获得

![image-20240123170006121](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123170006121.png)

![image-20240123170054486](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123170054486.png)

获取类的全部方法

```java
public void getDeclaredMethods(){
    // a.获取类对象
    Class c = Dog.class;
    // b.提取全部方法；包括私有的
    Method[] methods = c.getDeclaredMethods();
    // c.遍历全部方法
    for (Method method : methods) {
        System.out.println(method.getName() +" 返回值类型：" + method.getReturnType() + " 参数个数：" + method.getParameterCount());
    }
}
```

执行对象的方法invoke

![image-20240123170428209](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123170428209.png)

```java

//获取某个对象的方法
public void getDeclardMethod() throws Exception {
    // a.获取类对象
    Class c = Dog.class;
    // b.提取单个方法对象
    Method m = c.getDeclaredMethod("eat");
    Method m2 = c.getDeclaredMethod("eat", String.class);

    // 暴力打开权限了
    m.setAccessible(true);
    m2.setAccessible(true);

    // c.触发方法的执行
    Dog d = new Dog();
    // 注意：方法如果是没有结果回来的，那么返回的是null.
    Object result = m.invoke(d);
    System.out.println(result);

    Object result2 = m2.invoke(d, "骨头");
    System.out.println(result2);
}
```

### 反射的作用（补充）

1.绕过编译阶段位集合添加数据（如果已经确定泛型的集合，可以通过反射强制添加不同的元素）,确定泛型的时候是编译作用，**但是反射直接绕过了编译阶段在确定元素类型之前添加其他元素**

![image-20240123170614651](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123170614651.png)

```java
public static void main(String[] args) throws Exception {
    // 需求：反射实现泛型擦除后，加入其他类型的元素
    ArrayList<String> lists1 = new ArrayList<>();
    ArrayList<Integer> lists2 = new ArrayList<>();

    System.out.println(lists1.getClass());
    System.out.println(lists2.getClass());

    System.out.println(lists1.getClass() ==  lists2.getClass());  // ArrayList.class

    System.out.println("---------------------------");
    ArrayList<Integer> lists3 = new ArrayList<>();
    lists3.add(23);
    lists3.add(22);
    // lists3.add("黑马");
		
  //先获取list3的对象
    Class c = lists3.getClass(); // ArrayList.class  ===> public boolean add(E e)
    // 定位c类获取add方法
    Method add = c.getDeclaredMethod("add", Object.class);
    boolean rs = (boolean) add.invoke(lists3, "黑马");
    System.out.println(rs);

    System.out.println(lists3);

  //另外一种获取反射的方法，直接将引用交给另外一个对象
    ArrayList list4 = lists3;
    list4.add("白马");
    list4.add(false);
    System.out.println(lists3);
}
```

输出结果

![image-20240123171204412](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123171204412.png)

**2.反射在通用框架的作用**（先了解）

数据在存入数据库时不知道对象的类型，于是通过反射来装取

![image-20240123171450823](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123171450823.png)

```java
//用反射存取所有位置类型的对象


public static void save(Object obj){
    try (
            PrintStream ps = new PrintStream(new FileOutputStream("junit-reflect-annotation-proxy-app/src/data.txt", true));
    ){
        // 1、提取这个对象的全部成员变量：只有反射可以解决
        Class c = obj.getClass();  //   c.getSimpleName()获取当前类名   c.getName获取全限名：包名+类名
        ps.println("================" + c.getSimpleName() + "================");

        // 2、提取它的全部成员变量
        Field[] fields = c.getDeclaredFields();
        // 3、获取成员变量的信息
        for (Field field : fields) {
            String name = field.getName();
            // 提取本成员变量在obj对象中的值（取值）
            field.setAccessible(true);
            String value = field.get(obj) + "";
            ps.println(name  + "=" + value);
        }
    } catch (Exception e) {
        e.printStackTrace();
    }
}
```

## 注解

![image-20240123172739447](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123172739447.png)

### 自定义注解

格式

![image-20240123172859027](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123172859027.png)

```java
//定义注解

public @interface MyBook {
    String name();
    String[] authors();
    double price();
}
public @interface Book {
    String value(); // 特殊属性
    double price() ;
    //double price() default 9.9;
}

```

```java
@MyBook(name="《精通JavaSE》",authors = {"黑马", "dlei"} , price = 199.5)
//@Book(value = "/delete")
// @Book("/delete")
@Book(value = "/delete", price = 23.5)
//@Book("/delete")
public class AnnotationDemo1 {

    @MyBook(name="《精通JavaSE2》",authors = {"黑马", "dlei"} , price = 199.5)
    private AnnotationDemo1(){

    }

    @MyBook(name="《精通JavaSE1》",authors = {"黑马", "dlei"} , price = 199.5)
    public static void main(String[] args) {
        @MyBook(name="《精通JavaSE2》",authors = {"黑马", "dlei"} , price = 199.5)
        int age = 21;
    }
}
```

### 元注解（了解）

![image-20240123173519480](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123173519480.png)

![image-20240123195323473](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123195323473.png)

注解解析

Annotation，所有注解的抽象类，所有注解都是这个接口的实现类

![image-20240123201602342](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123201602342.png)

接口实现的方法

![image-20240123201627686](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123201627686.png)

解析注解的技巧

![image-20240123202033342](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123202033342.png)

![image-20240123204237547](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240123204237547.png)



 解析注解

```java
@Target({ElementType.TYPE,ElementType.METHOD})
@Retention(RetentionPolicy.RUNTIME)
public @interface Bookk {
    String value();
    double price() default 100;
    String[] author();
}
```

```java
public class AnnotationDemo3 {
    @Test
    public void parseClass(){
        // a.先得到类对象
        Class c = BookStore.class;
        // b.判断这个类上面是否存在这个注解
        if(c.isAnnotationPresent(Bookk.class)){
            //c.直接获取该注解对象
            Bookk book = (Bookk) c.getDeclaredAnnotation(Bookk.class);
            System.out.println(book.value());
            System.out.println(book.price());
            System.out.println(Arrays.toString(book.author()));
        }
    }

    @Test
    public void parseMethod() throws NoSuchMethodException {
        // a.先得到类对象
        Class c = BookStore.class;

        Method m = c.getDeclaredMethod("test");

        // b.判断这个类上面是否存在这个注解
        if(m.isAnnotationPresent(Bookk.class)){
            //c.直接获取该注解对象
            Bookk book = (Bookk) m.getDeclaredAnnotation(Bookk.class);
            System.out.println(book.value());
            System.out.println(book.price());
            System.out.println(Arrays.toString(book.author()));
        }
    }
}

@Bookk(value = "《情深深雨濛濛》", price = 99.9, author = {"琼瑶", "dlei"})
class BookStore{

    @Bookk(value = "《三少爷的剑》", price = 399.9, author = {"古龙", "熊耀华"})
    public void test(){
    }
}
```

## 动态代理

![image-20240124140547513](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124140547513.png)

![image-20240124142317738](/Users/xiechen/Library/Application Support/typora-user-images/image-20240124142317738.png)

代码实现

![image-20240124142807318](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124142807318.png)

## XML

![image-20240124150811924](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124150811924.png)

![image-20240124150942134](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124150942134.png)

![image-20240124151117452](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124151117452.png)

文档约束

DTD文档（不约束数据类型）

![image-20240124151325267](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124151325267.png)

schema

![image-20240124151644072](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124151644072.png)

### 解析XML文件

DOM

![image-20240124152102020](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124152102020.png)

拿去Document对象

![image-20240124152320281](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124152320281.png)

![image-20240124152345785](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124152345785.png)

这些对象都实现了Node接口

实例![image-20240124152457713](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124152457713.png)

方法类

![image-20240124153229905](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124153229905.png)

![image-20240124153750194](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124153750194.png)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<contactList>
    <contact id="1" vip="true">
        <name>   潘金莲  </name>
        <gender>女</gender>
        <email>panpan@itcast.cn</email>
    </contact>
    <contact id="2" vip="false">
        <name>武松</name>
        <gender>男</gender>
        <email>wusong@itcast.cn</email>
    </contact>
    <contact id="3" vip="false">
        <name>武大狼</name>
        <gender>男</gender>
        <email>wuda@itcast.cn</email>
    </contact>
    <user>
    </user>
</contactList>
```

```java
package com.itheima.d1_dom4j;

import org.dom4j.Attribute;
import org.dom4j.Document;
import org.dom4j.DocumentException;
import org.dom4j.Element;
import org.dom4j.io.SAXReader;
import org.junit.Test;

import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;
import java.util.List;

/**
   目标：学会使用dom4j解析XML文件中的数据。
    1、导入dom4j框架。
    2、准备一个XML文件。
 */
public class Dom4JHelloWorldDemo1 {
    @Test
    public void parseXMLData() throws Exception {
        // 1、创建一个Dom4j的解析器对象，代表了整个dom4j框架
        SAXReader saxReader = new SAXReader();

        // 2、把XML文件加载到内存中成为一个Document文档对象
        // Document document = saxReader.read(new File("xml-app\\src\\Contacts.xml")); // 需要通过模块名去定位
        // Document document = saxReader.read(new FileInputStream("xml-app\\src\\Contacts.xml"));

        // 注意: getResourceAsStream中的/是直接去src下寻找的文件
        InputStream is = Dom4JHelloWorldDemo1.class.getResourceAsStream("/Contacts.xml");
        Document document = saxReader.read(is);

        // 3、获取根元素对象
        Element root = document.getRootElement();
        System.out.println(root.getName());

        // 4、拿根元素下的全部子元素对象(一级)
        // List<Element> sonEles =  root.elements();
        List<Element> sonEles =  root.elements("contact");
        for (Element sonEle : sonEles) {
            System.out.println(sonEle.getName());
        }

        // 拿某个子元素
        Element userEle = root.element("user");
        System.out.println(userEle.getName());

        // 默认提取第一个子元素对象 (Java语言。)
        Element contact = root.element("contact");
        // 获取子元素文本
        System.out.println(contact.elementText("name"));
        // 去掉前后空格
        System.out.println(contact.elementTextTrim("name"));
        // 获取当前元素下的子元素对象
        Element email = contact.element("email");
        System.out.println(email.getText());
        // 去掉前后空格
        System.out.println(email.getTextTrim());

        // 根据元素获取属性值
        Attribute idAttr = contact.attribute("id");
        System.out.println(idAttr.getName() + "-->" + idAttr.getValue());
        // 直接提取属性值
        System.out.println(contact.attributeValue("id"));
        System.out.println(contact.attributeValue("vip"));




    }
}
```

解析联系人对象

```java
package com.itheima.d1_dom4j;

import org.dom4j.Document;
import org.dom4j.Element;
import org.dom4j.io.SAXReader;
import org.junit.Test;

import java.util.ArrayList;
import java.util.List;

public class Dom4JTest2 {
    @Test
    public void parseToList() throws Exception {
        // 需求：解析XML中的数据成为一个List集合对象。
        // 1、导入框架（做过）
        // 2、创建SaxReader对象
        SAXReader saxReader = new SAXReader();
        // 3、加载XML文件成为文档对象Document对象。
        Document document =
                saxReader.read(Dom4JTest2.class.getResourceAsStream("/Contacts.xml"));
        // 4、先拿根元素
        Element root = document.getRootElement();
        // 5、提取contact子元素
        List<Element> contactEles = root.elements("contact");
        // 6、准备一个ArrayList集合封装联系人信息
        List<Contact> contacts = new ArrayList<>();
        // 7、遍历Contact子元素
        for (Element contactEle : contactEles) {
            // 8、每个子元素都是一个联系人对象
            Contact contact = new Contact();
            contact.setId(Integer.valueOf(contactEle.attributeValue("id")));
            contact.setVip(Boolean.valueOf(contactEle.attributeValue("vip")));
            contact.setName(contactEle.elementTextTrim("name"));
            contact.setGender(contactEle.elementTextTrim("gender").charAt(0));
            contact.setEmail(contactEle.elementText("email"));
            // 9、把联系人对象数据加入到List集合
            contacts.add(contact);
        }
        // 10、遍历List集合
        for (Contact contact : contacts) {
            System.out.println(contact);
        }
    }
}
```

### XML的检索技术（基于Dom4j）

XPath-------jaxen.jar(自行下载)

常用api

![image-20240124155327352](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240124155327352.png)

```java
public class XPathDemo {
    /**
     1.绝对路径: /根元素/子元素/子元素。
     */
    @Test
    public void parse01() throws Exception {
        // a、创建解析器对象
        SAXReader saxReader = new SAXReader();
        // b、把XML加载成Document文档对象
        Document document =
                saxReader.read(XPathDemo.class.getResourceAsStream("/Contacts2.xml"));
        // c、检索全部的名称
        List<Node> nameNodes = document.selectNodes("/contactList/contact/name");
        for (Node nameNode : nameNodes) {
            Element  nameEle = (Element) nameNode;
            System.out.println(nameEle.getTextTrim());
        }
    }

    /**
     2.相对路径： ./子元素/子元素。 (.代表了当前元素)
     */
    @Test
    public void parse02() throws Exception {
        // a、创建解析器对象
        SAXReader saxReader = new SAXReader();
        // b、把XML加载成Document文档对象
        Document document =
                saxReader.read(XPathDemo.class.getResourceAsStream("/Contacts2.xml"));
        Element root = document.getRootElement();
        // c、检索全部的名称
        List<Node> nameNodes = root.selectNodes("./contact/name");
        for (Node nameNode : nameNodes) {
            Element  nameEle = (Element) nameNode;
            System.out.println(nameEle.getTextTrim());
        }
    }

    /**
     3.全文搜索：
     //元素  在全文找这个元素
     //元素1/元素2  在全文找元素1下面的一级元素2
     //元素1//元素2  在全文找元素1下面的全部元素2
     */
    @Test
    public void parse03() throws Exception {
        // a、创建解析器对象
        SAXReader saxReader = new SAXReader();
        // b、把XML加载成Document文档对象
        Document document =
                saxReader.read(XPathDemo.class.getResourceAsStream("/Contacts2.xml"));
        // c、检索数据
        //List<Node> nameNodes = document.selectNodes("//name");
        // List<Node> nameNodes = document.selectNodes("//contact/name");
        List<Node> nameNodes = document.selectNodes("//contact//name");
        for (Node nameNode : nameNodes) {
            Element  nameEle = (Element) nameNode;
            System.out.println(nameEle.getTextTrim());
        }
    }

    /**
     4.属性查找。
     //@属性名称  在全文检索属性对象。
     //元素[@属性名称]  在全文检索包含该属性的元素对象。
     //元素[@属性名称=值]  在全文检索包含该属性的元素且属性值为该值的元素对象。
     */
    @Test
    public void parse04() throws Exception {
        // a、创建解析器对象
        SAXReader saxReader = new SAXReader();
        // b、把XML加载成Document文档对象
        Document document =
                saxReader.read(XPathDemo.class.getResourceAsStream("/Contacts2.xml"));
        // c、检索数据
        List<Node> nodes = document.selectNodes("//@id");
        for (Node node : nodes) {
            Attribute attr = (Attribute) node;
            System.out.println(attr.getName() + "===>" + attr.getValue());
        }

        // 查询name元素（包含id属性的）
//      Node node = document.selectSingleNode("//name[@id]");
        Node node = document.selectSingleNode("//name[@id=888]");
        Element ele = (Element) node;
        System.out.println(ele.getTextTrim());
    }
}
```

检索的xml如下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<contactList>
    <contact id="1" vip="true">
        <name>   潘金莲  </name>
        <gender>女</gender>
        <email>panpan@itcast.cn</email>
    </contact>
    <contact id="2" vip="false">
        <name>武松</name>
        <gender>男</gender>
        <email>wusong@itcast.cn</email>
    </contact>
    <contact id="3" vip="false">
        <name>武大狼</name>
        <gender>男</gender>
        <email>wuda@itcast.cn</email>
    </contact>
    <user>
        <contact>
            <info>
                <name id="888">我是西门庆</name>
            </info>
         </contact>
    </user>
</contactList>
```

## JDBC

**今日目标**

> * 掌握JDBC的的CRUD
> * 理解JDBC中各个对象的作用
> * 掌握Druid的使用

## 1，JDBC概述

在开发中我们使用的是java语言，那么势必要通过java语言操作数据库中的数据。这就是接下来要学习的JDBC。

### 1.1  JDBC概念

> JDBC   就是使用Java语言操作关系型数据库的一套API
>
> 全称：( Java DataBase Connectivity ) Java 数据库连接

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725130537815.png" alt="image-20210725130537815" style="zoom:80%;" />

我们开发的同一套Java代码是无法操作不同的关系型数据库，因为每一个关系型数据库的底层实现细节都不一样。如果这样，问题就很大了，在公司中可以在开发阶段使用的是MySQL数据库，而上线时公司最终选用oracle数据库，我们就需要对代码进行大批量修改，这显然并不是我们想看到的。我们要做到的是同一套Java代码操作不同的关系型数据库，而此时sun公司就指定了一套标准接口（JDBC），JDBC中定义了所有操作关系型数据库的规则。众所周知接口是无法直接使用的，我们需要使用接口的实现类，而这套实现类（称之为：驱动）就由各自的数据库厂商给出。

### 1.2  JDBC本质

* 官方（sun公司）定义的一套操作所有关系型数据库的规则，即接口
* 各个数据库厂商去实现这套接口，提供数据库驱动jar包
* 我们可以使用这套接口（JDBC）编程，真正执行的代码是驱动jar包中的实现类

### 1.3  JDBC好处

* 各数据库厂商使用相同的接口，Java代码不需要针对不同数据库分别开发
* 可随时替换底层数据库，访问数据库的Java代码基本不变

以后编写操作数据库的代码只需要面向JDBC（接口），操作哪儿个关系型数据库就需要导入该数据库的驱动包，如需要操作MySQL数据库，就需要再项目中导入MySQL数据库的驱动包。如下图就是MySQL驱动包

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725133015535.png" alt="image-20210725133015535" style="zoom:90%;" />

## 2，JDBC快速入门

先来看看通过Java操作数据库的流程

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725163745153.png" alt="image-20210725163745153" style="zoom:80%;" />

第一步：编写Java代码

第二步：Java代码将SQL发送到MySQL服务端

第三步：MySQL服务端接收到SQL语句并执行该SQL语句

第四步：将SQL语句执行的结果返回给Java代码

### 2.1  编写代码步骤

* 创建工程，导入驱动jar包

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725133015535.png" alt="image-20210725133015535" style="zoom:90%;" />

* 注册驱动

  ```sql
  Class.forName("com.mysql.jdbc.Driver");
  ```

* 获取连接

  ```sql
  Connection conn = DriverManager.getConnection(url, username, password);
  ```

  Java代码需要发送SQL给MySQL服务端，就需要先建立连接

* 定义SQL语句

  ```sql
  String sql =  “update…” ;
  ```

* 获取执行SQL对象

  执行SQL语句需要SQL执行对象，而这个执行对象就是Statement对象

  ```sql
  Statement stmt = conn.createStatement();
  ```

* 执行SQL

  ```sql
  stmt.executeUpdate(sql);  
  ```

* 处理返回结果

* 释放资源

### 2.2  具体操作

* 创建新的空的项目

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725165156501.png" alt="image-20210725165156501" style="zoom:70%;" />

* 定义项目的名称，并指定位置

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725165220829.png" alt="image-20210725165220829" style="zoom:70%;" />

* 对项目进行设置，JDK版本、编译版本

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725165349564.png" alt="image-20210725165349564" style="zoom:70%;" />

* 创建模块，指定模块的名称及位置

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725165536898.png" alt="image-20210725165536898" style="zoom:70%;" />

* 导入驱动包

  将mysql的驱动包放在模块下的lib目录（随意命名）下，并将该jar包添加为库文件

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725165657556.png" alt="image-20210725165657556" style="zoom:80%;" />

* 在添加为库文件的时候，有如下三个选项
  * Global Library  ： 全局有效
  * Project Library :   项目有效
  * Module Library ： 模块有效

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725165751273.png" alt="image-20210725165751273" style="zoom:80%;" />

* 在src下创建类

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725170004319.png" alt="image-20210725170004319" style="zoom:70%;" />

* 编写代码如下

```java
/**
 * JDBC快速入门
 */
public class JDBCDemo {

    public static void main(String[] args) throws Exception {
        //1. 注册驱动
        //Class.forName("com.mysql.jdbc.Driver");
        //2. 获取连接
        String url = "jdbc:mysql://127.0.0.1:3306/db1";
        String username = "root";
        String password = "1234";
        Connection conn = DriverManager.getConnection(url, username, password);
        //3. 定义sql
        String sql = "update account set money = 2000 where id = 1";
        //4. 获取执行sql的对象 Statement
        Statement stmt = conn.createStatement();
        //5. 执行sql
        int count = stmt.executeUpdate(sql);//受影响的行数
        //6. 处理结果
        System.out.println(count);
        //7. 释放资源
        stmt.close();
        conn.close();
    }
}
```



## 3，JDBC API详解

### 3.1  DriverManager

DriverManager（驱动管理类）作用：

* 注册驱动

  ![image-20210725171339346](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725171339346.png)

  registerDriver方法是用于注册驱动的，但是我们之前做的入门案例并不是这样写的。而是如下实现

  ```sql
  Class.forName("com.mysql.jdbc.Driver");
  ```

  我们查询MySQL提供的Driver类，看它是如何实现的，源码如下：

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725171635432.png" alt="image-20210725171635432" style="zoom:70%;" />

  在该类中的静态代码块中已经执行了 `DriverManager` 对象的 `registerDriver()` 方法进行驱动的注册了，那么我们只需要加载 `Driver` 类，该静态代码块就会执行。而 `Class.forName("com.mysql.jdbc.Driver");` 就可以加载 `Driver` 类。

  > ==提示：==
  >
  > * MySQL 5之后的驱动包，可以省略注册驱动的步骤
  > * 自动加载jar包中META-INF/services/java.sql.Driver文件中的驱动类

* 获取数据库连接

  ![image-20210725171355278](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725171355278.png)

  参数说明：

  * url ： 连接路径

    > 语法：jdbc:mysql://ip地址(域名):端口号/数据库名称?参数键值对1&参数键值对2…
    >
    > 示例：jdbc:mysql://127.0.0.1:3306/db1
    >
    > ==细节：==
    >
    > * 如果连接的是本机mysql服务器，并且mysql服务默认端口是3306，则url可以简写为：jdbc:mysql:///数据库名称?参数键值对
    >
    > * 配置 useSSL=false 参数，禁用安全连接方式，解决警告提示

  * user ：用户名

  * poassword ：密码

### 3.2  Connection

Connection（数据库连接对象）作用：

* 获取执行 SQL 的对象
* 管理事务

#### 3.2.1  获取执行对象

* 普通执行SQL对象

  ```sql
  Statement createStatement()
  ```

  入门案例中就是通过该方法获取的执行对象。

* 预编译SQL的执行SQL对象：防止SQL注入

  ```sql
  PreparedStatement  prepareStatement(sql)
  ```

  通过这种方式获取的 `PreparedStatement` SQL语句执行对象是我们一会重点要进行讲解的，它可以防止SQL注入。

* 执行存储过程的对象

  ```sql
  CallableStatement prepareCall(sql)
  ```

  通过这种方式获取的 `CallableStatement` 执行对象是用来执行存储过程的，而存储过程在MySQL中不常用，所以这个我们将不进行讲解。

#### 3.2.2  事务管理

先回顾一下MySQL事务管理的操作：

* 开启事务 ： BEGIN; 或者 START TRANSACTION;
* 提交事务 ： COMMIT;
* 回滚事务 ： ROLLBACK;

> MySQL默认是自动提交事务

接下来学习JDBC事务管理的方法。

Connection几口中定义了3个对应的方法：

* 开启事务

  ![image-20210725173444628](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725173444628.png)

  参与autoCommit 表示是否自动提交事务，true表示自动提交事务，false表示手动提交事务。而开启事务需要将该参数设为为false。

* 提交事务

  ![image-20210725173618636](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725173618636.png)

* 回滚事务

  ![image-20210725173648674](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725173648674.png)

具体代码实现如下：

```sql
/**
 * JDBC API 详解：Connection
 */
public class JDBCDemo3_Connection {

    public static void main(String[] args) throws Exception {
        //1. 注册驱动
        //Class.forName("com.mysql.jdbc.Driver");
        //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
        String url = "jdbc:mysql:///db1?useSSL=false";
        String username = "root";
        String password = "1234";
        Connection conn = DriverManager.getConnection(url, username, password);
        //3. 定义sql
        String sql1 = "update account set money = 3000 where id = 1";
        String sql2 = "update account set money = 3000 where id = 2";
        //4. 获取执行sql的对象 Statement
        Statement stmt = conn.createStatement();

        try {
            // ============开启事务==========
            conn.setAutoCommit(false);
            //5. 执行sql
            int count1 = stmt.executeUpdate(sql1);//受影响的行数
            //6. 处理结果
            System.out.println(count1);
            int i = 3/0;
            //5. 执行sql
            int count2 = stmt.executeUpdate(sql2);//受影响的行数
            //6. 处理结果
            System.out.println(count2);

            // ============提交事务==========
            //程序运行到此处，说明没有出现任何问题，则需求提交事务
            conn.commit();
        } catch (Exception e) {
            // ============回滚事务==========
            //程序在出现异常时会执行到这个地方，此时就需要回滚事务
            conn.rollback();
            e.printStackTrace();
        }

        //7. 释放资源
        stmt.close();
        conn.close();
    }
}
```

### 3.3  Statement

#### 3.3.1  概述

Statement对象的作用就是用来执行SQL语句。而针对不同类型的SQL语句使用的方法也不一样。

* 执行DDL、DML语句

  ![image-20210725175151272](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725175151272.png)

* 执行DQL语句

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725175131533.png" alt="image-20210725175131533" style="zoom:80%;" />

  该方法涉及到了 `ResultSet` 对象，而这个对象我们还没有学习，一会再重点讲解。



#### 3.3.2  代码实现

* 执行DML语句

  ```java
  /**
    * 执行DML语句
    * @throws Exception
    */
  @Test
  public void testDML() throws  Exception {
      //1. 注册驱动
      //Class.forName("com.mysql.jdbc.Driver");
      //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
      String url = "jdbc:mysql:///db1?useSSL=false";
      String username = "root";
      String password = "1234";
      Connection conn = DriverManager.getConnection(url, username, password);
      //3. 定义sql
      String sql = "update account set money = 3000 where id = 1";
      //4. 获取执行sql的对象 Statement
      Statement stmt = conn.createStatement();
      //5. 执行sql
      int count = stmt.executeUpdate(sql);//执行完DML语句，受影响的行数
      //6. 处理结果
      //System.out.println(count);
      if(count > 0){
          System.out.println("修改成功~");
      }else{
          System.out.println("修改失败~");
      }
      //7. 释放资源
      stmt.close();
      conn.close();
  }
  ```

* 执行DDL语句

  ```java
  /**
    * 执行DDL语句
    * @throws Exception
    */
  @Test
  public void testDDL() throws  Exception {
      //1. 注册驱动
      //Class.forName("com.mysql.jdbc.Driver");
      //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
      String url = "jdbc:mysql:///db1?useSSL=false";
      String username = "root";
      String password = "1234";
      Connection conn = DriverManager.getConnection(url, username, password);
      //3. 定义sql
      String sql = "drop database db2";
      //4. 获取执行sql的对象 Statement
      Statement stmt = conn.createStatement();
      //5. 执行sql
      int count = stmt.executeUpdate(sql);//执行完DDL语句，可能是0
      //6. 处理结果
      System.out.println(count);
  
      //7. 释放资源
      stmt.close();
      conn.close();
  }
  ```

  > 注意：
  >
  > * 以后开发很少使用java代码操作DDL语句

### 3.4  ResultSet

#### 3.4.1  概述

ResultSet（结果集对象）作用：

* ==封装了SQL查询语句的结果。==

而执行了DQL语句后就会返回该对象，对应执行DQL语句的方法如下：

```sql
ResultSet  executeQuery(sql)：执行DQL 语句，返回 ResultSet 对象
```

那么我们就需要从 `ResultSet` 对象中获取我们想要的数据。`ResultSet` 对象提供了操作查询结果数据的方法，如下：

> boolean  next()
>
> * 将光标从当前位置向前移动一行 
> * 判断当前行是否为有效行
>
> 方法返回值说明：
>
> * true  ： 有效航，当前行有数据
> * false ： 无效行，当前行没有数据

> xxx  getXxx(参数)：获取数据
>
> * xxx : 数据类型；如： int getInt(参数) ；String getString(参数)
> * 参数
>   * int类型的参数：列的编号，从1开始
>   * String类型的参数： 列的名称 

如下图为执行SQL语句后的结果

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725181320813.png" alt="image-20210725181320813" style="zoom:80%;" />

一开始光标指定于第一行前，如图所示红色箭头指向于表头行。当我们调用了 `next()` 方法后，光标就下移到第一行数据，并且方法返回true，此时就可以通过 `getInt("id")` 获取当前行id字段的值，也可以通过 `getString("name")` 获取当前行name字段的值。如果想获取下一行的数据，继续调用 `next()`  方法，以此类推。

#### 3.4.2  代码实现

```java
/**
  * 执行DQL
  * @throws Exception
  */
@Test
public void testResultSet() throws  Exception {
    //1. 注册驱动
    //Class.forName("com.mysql.jdbc.Driver");
    //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
    String url = "jdbc:mysql:///db1?useSSL=false";
    String username = "root";
    String password = "1234";
    Connection conn = DriverManager.getConnection(url, username, password);
    //3. 定义sql
    String sql = "select * from account";
    //4. 获取statement对象
    Statement stmt = conn.createStatement();
    //5. 执行sql
    ResultSet rs = stmt.executeQuery(sql);
    //6. 处理结果， 遍历rs中的所有数据
    /* // 6.1 光标向下移动一行，并且判断当前行是否有数据
        while (rs.next()){
            //6.2 获取数据  getXxx()
            int id = rs.getInt(1);
            String name = rs.getString(2);
            double money = rs.getDouble(3);

            System.out.println(id);
            System.out.println(name);
            System.out.println(money);

            System.out.println("--------------");

        }*/
    // 6.1 光标向下移动一行，并且判断当前行是否有数据
    while (rs.next()){
        //6.2 获取数据  getXxx()
        int id = rs.getInt("id");
        String name = rs.getString("name");
        double money = rs.getDouble("money");

        System.out.println(id);
        System.out.println(name);
        System.out.println(money);

        System.out.println("--------------");
    }

    //7. 释放资源
    rs.close();
    stmt.close();
    conn.close();
}
```

### 3.5  案例

* 需求：查询account账户表数据，封装为Account对象中，并且存储到ArrayList集合中

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725182352433.png" alt="image-20210725182352433" style="zoom:80%;" />

* 代码实现

  ```java
  /**
    * 查询account账户表数据，封装为Account对象中，并且存储到ArrayList集合中
    * 1. 定义实体类Account
    * 2. 查询数据，封装到Account对象中
    * 3. 将Account对象存入ArrayList集合中
    */
  @Test
  public void testResultSet2() throws  Exception {
      //1. 注册驱动
      //Class.forName("com.mysql.jdbc.Driver");
      //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
      String url = "jdbc:mysql:///db1?useSSL=false";
      String username = "root";
      String password = "1234";
      Connection conn = DriverManager.getConnection(url, username, password);
  
      //3. 定义sql
      String sql = "select * from account";
  
      //4. 获取statement对象
      Statement stmt = conn.createStatement();
  
      //5. 执行sql
      ResultSet rs = stmt.executeQuery(sql);
  
      // 创建集合
      List<Account> list = new ArrayList<>();
     
      // 6.1 光标向下移动一行，并且判断当前行是否有数据
      while (rs.next()){
          Account account = new Account();
  
          //6.2 获取数据  getXxx()
          int id = rs.getInt("id");
          String name = rs.getString("name");
          double money = rs.getDouble("money");
  
          //赋值
          account.setId(id);
          account.setName(name);
          account.setMoney(money);
  
          // 存入集合
          list.add(account);
      }
  
      System.out.println(list);
  
      //7. 释放资源
      rs.close();
      stmt.close();
      conn.close();
  }
  ```



### 3.6  PreparedStatement

> PreparedStatement作用：
>
> * 预编译SQL语句并执行：预防SQL注入问题

对上面的作用中SQL注入问题大家肯定不理解。那我们先对SQL注入进行说明.

#### 3.6.1  SQL注入

> SQL注入是通过操作输入来修改事先定义好的SQL语句，用以达到执行代码对服务器进行攻击的方法。

在今天资料下的 `day03-JDBC\资料\2. sql注入演示` 中修改 `application.properties` 文件中的用户名和密码，文件内容如下：

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/test?useSSL=false&useUnicode=true&characterEncoding=UTF-8
spring.datasource.username=root
spring.datasource.password=1234
```

在MySQL中创建名为 `test` 的数据库

```sql
create database test;
```

在命令提示符中运行今天资料下的 `day03-JDBC\资料\2. sql注入演示\sql.jar` 这个jar包。

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725184701026.png" alt="image-20210725184701026" style="zoom:80%;" /> 

此时我们就能在数据库中看到user表

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725184817731.png" alt="image-20210725184817731" style="zoom:80%;" />

接下来在浏览器的地址栏输入 `localhost:8080/login.html` 就能看到如下页面

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725185024731.png" alt="image-20210725185024731" style="zoom:80%;" />

我们就可以在如上图中输入用户名和密码进行登陆。用户名和密码输入正确就登陆成功，跳转到首页。用户名和密码输入错误则给出错误提示，如下图

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725185320875.png" alt="image-20210725185320875" style="zoom:80%;" />

但是我可以通过输入一些特殊的字符登陆到首页。

用户名随意写，密码写成 `' or '1' ='1`

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725185603112.png" alt="image-20210725185603112" style="zoom:80%;" />

这就是SQL注入漏洞，也是很危险的。当然现在市面上的系统都不会存在这种问题了，所以大家也不要尝试用这种方式去试其他的系统。

那么该如何解决呢？这里就可以将SQL执行对象 `Statement` 换成 `PreparedStatement` 对象。

#### 3.6.2  代码模拟SQL注入问题

```java
@Test
public void testLogin() throws  Exception {
    //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
    String url = "jdbc:mysql:///db1?useSSL=false";
    String username = "root";
    String password = "1234";
    Connection conn = DriverManager.getConnection(url, username, password);

    // 接收用户输入 用户名和密码
    String name = "sjdljfld";
    String pwd = "' or '1' = '1";
    String sql = "select * from tb_user where username = '"+name+"' and password = '"+pwd+"'";
    // 获取stmt对象
    Statement stmt = conn.createStatement();
    // 执行sql
    ResultSet rs = stmt.executeQuery(sql);
    // 判断登录是否成功
    if(rs.next()){
        System.out.println("登录成功~");
    }else{
        System.out.println("登录失败~");
    }

    //7. 释放资源
    rs.close();
    stmt.close();
    conn.close();
}
```

上面代码是将用户名和密码拼接到sql语句中，拼接后的sql语句如下

```sql
select * from tb_user where username = 'sjdljfld' and password = ''or '1' = '1'
```

从上面语句可以看出条件 `username = 'sjdljfld' and password = ''` 不管是否满足，而 `or` 后面的 `'1' = '1'` 是始终满足的，最终条件是成立的，就可以正常的进行登陆了。

接下来我们来学习PreparedStatement对象.

#### 3.6.3  PreparedStatement概述

> PreparedStatement作用：
>
> * 预编译SQL语句并执行：预防SQL注入问题

* 获取 PreparedStatement 对象

  ```java
  // SQL语句中的参数值，使用？占位符替代
  String sql = "select * from user where username = ? and password = ?";
  // 通过Connection对象获取，并传入对应的sql语句
  PreparedStatement pstmt = conn.prepareStatement(sql);
  ```

* 设置参数值

  上面的sql语句中参数使用 ? 进行占位，在之前之前肯定要设置这些 ?  的值。

  > PreparedStatement对象：setXxx(参数1，参数2)：给 ? 赋值
  >
  > * Xxx：数据类型 ； 如 setInt (参数1，参数2)
  >
  > * 参数：
  >
  >   * 参数1： ？的位置编号，从1 开始
  >
  >   * 参数2： ？的值

* 执行SQL语句

  > executeUpdate();  执行DDL语句和DML语句
  >
  > executeQuery();  执行DQL语句
  >
  > ==注意：==
  >
  > * 调用这两个方法时不需要传递SQL语句，因为获取SQL语句执行对象时已经对SQL语句进行预编译了。

#### 3.6.4  使用PreparedStatement改进

```java
 @Test
public void testPreparedStatement() throws  Exception {
    //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
    String url = "jdbc:mysql:///db1?useSSL=false";
    String username = "root";
    String password = "1234";
    Connection conn = DriverManager.getConnection(url, username, password);

    // 接收用户输入 用户名和密码
    String name = "zhangsan";
    String pwd = "' or '1' = '1";

    // 定义sql
    String sql = "select * from tb_user where username = ? and password = ?";
    // 获取pstmt对象
    PreparedStatement pstmt = conn.prepareStatement(sql);
    // 设置？的值
    pstmt.setString(1,name);
    pstmt.setString(2,pwd);
    // 执行sql
    ResultSet rs = pstmt.executeQuery();
    // 判断登录是否成功
    if(rs.next()){
        System.out.println("登录成功~");
    }else{
        System.out.println("登录失败~");
    }
    //7. 释放资源
    rs.close();
    pstmt.close();
    conn.close();
}
```

执行上面语句就可以发现不会出现SQL注入漏洞问题了。那么PreparedStatement又是如何解决的呢？它是将特殊字符进行了转义，转义的SQL如下：

```sql
select * from tb_user where username = 'sjdljfld' and password = '\'or \'1\' = \'1'
```



#### 3.6.5  PreparedStatement原理

> PreparedStatement 好处：
>
> * 预编译SQL，性能更高
> * 防止SQL注入：==将敏感字符进行转义==

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725195756848.png" alt="image-20210725195756848" style="zoom:80%;" />

Java代码操作数据库流程如图所示：

* 将sql语句发送到MySQL服务器端

* MySQL服务端会对sql语句进行如下操作

  * 检查SQL语句

    检查SQL语句的语法是否正确。

  * 编译SQL语句。将SQL语句编译成可执行的函数。

    检查SQL和编译SQL花费的时间比执行SQL的时间还要长。如果我们只是重新设置参数，那么检查SQL语句和编译SQL语句将不需要重复执行。这样就提高了性能。

  * 执行SQL语句

接下来我们通过查询日志来看一下原理。

* 开启预编译功能

  在代码中编写url时需要加上以下参数。而我们之前根本就没有开启预编译功能，只是解决了SQL注入漏洞。

  ```sql
  useServerPrepStmts=true
  ```

* 配置MySQL执行日志（重启mysql服务后生效）

  在mysql配置文件（my.ini）中添加如下配置

  ```
  log-output=FILE
  general-log=1
  general_log_file="D:\mysql.log"
  slow-query-log=1
  slow_query_log_file="D:\mysql_slow.log"
  long_query_time=2
  ```

* java测试代码如下：

  ```java
   /**
     * PreparedStatement原理
     * @throws Exception
     */
  @Test
  public void testPreparedStatement2() throws  Exception {
  
      //2. 获取连接：如果连接的是本机mysql并且端口是默认的 3306 可以简化书写
      // useServerPrepStmts=true 参数开启预编译功能
      String url = "jdbc:mysql:///db1?useSSL=false&useServerPrepStmts=true";
      String username = "root";
      String password = "1234";
      Connection conn = DriverManager.getConnection(url, username, password);
  
      // 接收用户输入 用户名和密码
      String name = "zhangsan";
      String pwd = "' or '1' = '1";
  
      // 定义sql
      String sql = "select * from tb_user where username = ? and password = ?";
  
      // 获取pstmt对象
      PreparedStatement pstmt = conn.prepareStatement(sql);
  
      Thread.sleep(10000);
      // 设置？的值
      pstmt.setString(1,name);
      pstmt.setString(2,pwd);
      ResultSet rs = null;
      // 执行sql
      rs = pstmt.executeQuery();
  
      // 设置？的值
      pstmt.setString(1,"aaa");
      pstmt.setString(2,"bbb");
      // 执行sql
      rs = pstmt.executeQuery();
  
      // 判断登录是否成功
      if(rs.next()){
          System.out.println("登录成功~");
      }else{
          System.out.println("登录失败~");
      }
  
      //7. 释放资源
      rs.close();
      pstmt.close();
      conn.close();
  }
  ```

  

* 执行SQL语句，查看 `D:\mysql.log` 日志如下:

  ![image-20210725202829738](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725202829738.png)

  上图中第三行中的 `Prepare` 是对SQL语句进行预编译。第四行和第五行是执行了两次SQL语句，而第二次执行前并没有对SQL进行预编译。

> ==小结：==
>
> * 在获取PreparedStatement对象时，将sql语句发送给mysql服务器进行检查，编译（这些步骤很耗时）
> * 执行时就不用再进行这些步骤了，速度更快
> * 如果sql模板一样，则只需要进行一次检查、编译

## 4，数据库连接池

### 4.1  数据库连接池简介

> * 数据库连接池是个容器，负责分配、管理数据库连接(Connection)
>
> * 它允许应用程序重复使用一个现有的数据库连接，而不是再重新建立一个；
>
> * 释放空闲时间超过最大空闲时间的数据库连接来避免因为没有释放数据库连接而引起的数据库连接遗漏
> * 好处
>   * 资源重用
>   * 提升系统响应速度
>   * 避免数据库连接遗漏

之前我们代码中使用连接是没有使用都创建一个Connection对象，使用完毕就会将其销毁。这样重复创建销毁的过程是特别耗费计算机的性能的及消耗时间的。

而数据库使用了数据库连接池后，就能达到Connection对象的复用，如下图

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725210432985.png" alt="image-20210725210432985" style="zoom:80%;" />

连接池是在一开始就创建好了一些连接（Connection）对象存储起来。用户需要连接数据库时，不需要自己创建连接，而只需要从连接池中获取一个连接进行使用，使用完毕后再将连接对象归还给连接池；这样就可以起到资源重用，也节省了频繁创建连接销毁连接所花费的时间，从而提升了系统响应的速度。

### 4.2  数据库连接池实现

* 标准接口：==DataSource==

  官方(SUN) 提供的数据库连接池标准接口，由第三方组织实现此接口。该接口提供了获取连接的功能：

  ```java
  Connection getConnection()
  ```

  那么以后就不需要通过 `DriverManager` 对象获取 `Connection` 对象，而是通过连接池（DataSource）获取 `Connection` 对象。

* 常见的数据库连接池

  * DBCP
  * C3P0
  * Druid

  我们现在使用更多的是Druid，它的性能比其他两个会好一些。

* Druid（德鲁伊）

  * Druid连接池是阿里巴巴开源的数据库连接池项目 

  * 功能强大，性能优秀，是Java语言最好的数据库连接池之一

### 4.3  Driud使用

> * 导入jar包 druid-1.1.12.jar
> * 定义配置文件
> * 加载配置文件
> * 获取数据库连接池对象
> * 获取连接

现在通过代码实现，首先需要先将druid的jar包放到项目下的lib下并添加为库文件

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725212911980.png" alt="image-20210725212911980" style="zoom:80%;" />

项目结构如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210725213210091.png" alt="image-20210725213210091" style="zoom:80%;" />

编写配置文件如下：

```properties
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql:///db1?useSSL=false&useServerPrepStmts=true
username=root
password=1234
# 初始化连接数量
initialSize=5
# 最大连接数
maxActive=10
# 最大等待时间
maxWait=3000
```

使用druid的代码如下：

```java
/**
 * Druid数据库连接池演示
 */
public class DruidDemo {

    public static void main(String[] args) throws Exception {
        //1.导入jar包
        //2.定义配置文件
        //3. 加载配置文件
        Properties prop = new Properties();
        prop.load(new FileInputStream("jdbc-demo/src/druid.properties"));
        //4. 获取连接池对象
        DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);

        //5. 获取数据库连接 Connection
        Connection connection = dataSource.getConnection();
        System.out.println(connection); //获取到了连接后就可以继续做其他操作了

        //System.out.println(System.getProperty("user.dir"));
    }
}
```

## 5，JDBC练习

### 5.1  需求

完成商品品牌数据的增删改查操作

* 查询：查询所有数据
* 添加：添加品牌
* 修改：根据id修改
* 删除：根据id删除

### 5.2  案例实现

#### 5.2.1  环境准备

* 数据库表 `tb_brand`

  ```sql
  -- 删除tb_brand表
  drop table if exists tb_brand;
  -- 创建tb_brand表
  create table tb_brand (
      -- id 主键
      id int primary key auto_increment,
      -- 品牌名称
      brand_name varchar(20),
      -- 企业名称
      company_name varchar(20),
      -- 排序字段
      ordered int,
      -- 描述信息
      description varchar(100),
      -- 状态：0：禁用  1：启用
      status int
  );
  -- 添加数据
  insert into tb_brand (brand_name, company_name, ordered, description, status)
  values ('三只松鼠', '三只松鼠股份有限公司', 5, '好吃不上火', 0),
         ('华为', '华为技术有限公司', 100, '华为致力于把数字世界带入每个人、每个家庭、每个组织，构建万物互联的智能世界', 1),
         ('小米', '小米科技有限公司', 50, 'are you ok', 1);
  ```

* 在pojo包下实体类 Brand

  ```java
  /**
   * 品牌
   * alt + 鼠标左键：整列编辑
   * 在实体类中，基本数据类型建议使用其对应的包装类型
   */
  public class Brand {
      // id 主键
      private Integer id;
      // 品牌名称
      private String brandName;
      // 企业名称
      private String companyName;
      // 排序字段
      private Integer ordered;
      // 描述信息
      private String description;
      // 状态：0：禁用  1：启用
      private Integer status;
  
      public Integer getId() {
          return id;
      }
  
      public void setId(Integer id) {
          this.id = id;
      }
  
      public String getBrandName() {
          return brandName;
      }
  
      public void setBrandName(String brandName) {
          this.brandName = brandName;
      }
  
      public String getCompanyName() {
          return companyName;
      }
  
      public void setCompanyName(String companyName) {
          this.companyName = companyName;
      }
  
      public Integer getOrdered() {
          return ordered;
      }
  
      public void setOrdered(Integer ordered) {
          this.ordered = ordered;
      }
  
      public String getDescription() {
          return description;
      }
  
      public void setDescription(String description) {
          this.description = description;
      }
  
      public Integer getStatus() {
          return status;
      }
  
      public void setStatus(Integer status) {
          this.status = status;
      }
  
      @Override
      public String toString() {
          return "Brand{" +
                  "id=" + id +
                  ", brandName='" + brandName + '\'' +
                  ", companyName='" + companyName + '\'' +
                  ", ordered=" + ordered +
                  ", description='" + description + '\'' +
                  ", status=" + status +
                  '}';
      }
  }
  ```

#### 5.2.2  查询所有

```java
 /**
   * 查询所有
   * 1. SQL：select * from tb_brand;
   * 2. 参数：不需要
   * 3. 结果：List<Brand>
   */

@Test
public void testSelectAll() throws Exception {
    //1. 获取Connection
    //3. 加载配置文件
    Properties prop = new Properties();
    prop.load(new FileInputStream("jdbc-demo/src/druid.properties"));
    //4. 获取连接池对象
    DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);

    //5. 获取数据库连接 Connection
    Connection conn = dataSource.getConnection();
    //2. 定义SQL
    String sql = "select * from tb_brand;";
    //3. 获取pstmt对象
    PreparedStatement pstmt = conn.prepareStatement(sql);
    //4. 设置参数
    //5. 执行SQL
    ResultSet rs = pstmt.executeQuery();
    //6. 处理结果 List<Brand> 封装Brand对象，装载List集合
    Brand brand = null;
    List<Brand> brands = new ArrayList<>();
    while (rs.next()){
        //获取数据
        int id = rs.getInt("id");
        String brandName = rs.getString("brand_name");
        String companyName = rs.getString("company_name");
        int ordered = rs.getInt("ordered");
        String description = rs.getString("description");
        int status = rs.getInt("status");
        //封装Brand对象
        brand = new Brand();
        brand.setId(id);
        brand.setBrandName(brandName);
        brand.setCompanyName(companyName);
        brand.setOrdered(ordered);
        brand.setDescription(description);
        brand.setStatus(status);

        //装载集合
        brands.add(brand);
    }
    System.out.println(brands);
    //7. 释放资源
    rs.close();
    pstmt.close();
    conn.close();
}
```

#### 5.2.3  添加数据

```java
/**
  * 添加
  * 1. SQL：insert into tb_brand(brand_name, company_name, ordered, description, status) values(?,?,?,?,?);
  * 2. 参数：需要，除了id之外的所有参数信息
  * 3. 结果：boolean
  */
@Test
public void testAdd() throws Exception {
    // 接收页面提交的参数
    String brandName = "香飘飘";
    String companyName = "香飘飘";
    int ordered = 1;
    String description = "绕地球一圈";
    int status = 1;

    //1. 获取Connection
    //3. 加载配置文件
    Properties prop = new Properties();
    prop.load(new FileInputStream("jdbc-demo/src/druid.properties"));
    //4. 获取连接池对象
    DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);
    //5. 获取数据库连接 Connection
    Connection conn = dataSource.getConnection();
    //2. 定义SQL
    String sql = "insert into tb_brand(brand_name, company_name, ordered, description, status) values(?,?,?,?,?);";
    //3. 获取pstmt对象
    PreparedStatement pstmt = conn.prepareStatement(sql);
    //4. 设置参数
    pstmt.setString(1,brandName);
    pstmt.setString(2,companyName);
    pstmt.setInt(3,ordered);
    pstmt.setString(4,description);
    pstmt.setInt(5,status);

    //5. 执行SQL
    int count = pstmt.executeUpdate(); // 影响的行数
    //6. 处理结果
    System.out.println(count > 0);

    //7. 释放资源
    pstmt.close();
    conn.close();
}
```

#### 5.2.4  修改数据

```java
/**
  * 修改
  * 1. SQL：

     update tb_brand
         set brand_name  = ?,
         company_name= ?,
         ordered     = ?,
         description = ?,
         status      = ?
     where id = ?

   * 2. 参数：需要，所有数据
   * 3. 结果：boolean
   */

@Test
public void testUpdate() throws Exception {
    // 接收页面提交的参数
    String brandName = "香飘飘";
    String companyName = "香飘飘";
    int ordered = 1000;
    String description = "绕地球三圈";
    int status = 1;
    int id = 4;

    //1. 获取Connection
    //3. 加载配置文件
    Properties prop = new Properties();
    prop.load(new FileInputStream("jdbc-demo/src/druid.properties"));
    //4. 获取连接池对象
    DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);
    //5. 获取数据库连接 Connection
    Connection conn = dataSource.getConnection();
    //2. 定义SQL
    String sql = " update tb_brand\n" +
        "         set brand_name  = ?,\n" +
        "         company_name= ?,\n" +
        "         ordered     = ?,\n" +
        "         description = ?,\n" +
        "         status      = ?\n" +
        "     where id = ?";

    //3. 获取pstmt对象
    PreparedStatement pstmt = conn.prepareStatement(sql);

    //4. 设置参数
    pstmt.setString(1,brandName);
    pstmt.setString(2,companyName);
    pstmt.setInt(3,ordered);
    pstmt.setString(4,description);
    pstmt.setInt(5,status);
    pstmt.setInt(6,id);

    //5. 执行SQL
    int count = pstmt.executeUpdate(); // 影响的行数
    //6. 处理结果
    System.out.println(count > 0);

    //7. 释放资源
    pstmt.close();
    conn.close();
}
```

#### 5.2.5  删除数据

```java
/**
  * 删除
  * 1. SQL：
            delete from tb_brand where id = ?
  * 2. 参数：需要，id
  * 3. 结果：boolean
  */
@Test
public void testDeleteById() throws Exception {
    // 接收页面提交的参数
    int id = 4;
    //1. 获取Connection
    //3. 加载配置文件
    Properties prop = new Properties();
    prop.load(new FileInputStream("jdbc-demo/src/druid.properties"));
    //4. 获取连接池对象
    DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);
    //5. 获取数据库连接 Connection
    Connection conn = dataSource.getConnection();
    //2. 定义SQL
    String sql = " delete from tb_brand where id = ?";
    //3. 获取pstmt对象
    PreparedStatement pstmt = conn.prepareStatement(sql);
    //4. 设置参数
    pstmt.setInt(1,id);
    //5. 执行SQL
    int count = pstmt.executeUpdate(); // 影响的行数
    //6. 处理结果
    System.out.println(count > 0);

    //7. 释放资源
    pstmt.close();
    conn.close();
}
```

# Maven

![image-20240219202450721](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219202450721.png)

![image-20240219203201635](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219203201635.png)

![image-20240219203655109](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219203655109.png)

![image-20240219210257672](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219210257672.png)

![image-20240219215311920](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219215311920.png)

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219215329788.png)

![image-20240219215636523](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240219215636523.png)

# MyBatis



mybatis前置代码实例

![image-20240313182349667](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240313182349667.png)

## 查询

### resultMap查询

![image-20240307162220647](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240307162220647.png)

### 查看详情功能

![image-20240307162624399](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240307162624399.png)

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312153812506.png)

![image-20240312154139620](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312154139620.png)

### 条件查询

下面需要注意的就是需要表明一下多参数的映射关系

=号用于等值查询 like用于模糊查询，下面处理参数的方法就是模糊处理



![image-20240312155455988](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312155455988.png) 

![image-20240312155029207](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312155029207.png)

![image-20240312154601775](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312154601775.png)

总结

![image-20240312155851698](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312155851698.png)

### 动态查询sql

![image-20240312161758173](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312161758173.png)

![image-20240312204117788](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312204117788.png)

### 单条件动态查询

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312204348929.png)

## 添加

### 基础添加

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312210024405.png)

### 主键返回

获取添加之后的id

设置下面参数，就可以获取返回值，返回的是添加的id，keyProperty设置返回的主键

![image-20240312214023710](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312214023710.png)

![image-20240312213931475](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312213931475.png)

![image-20240312214106054](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312214106054.png)

## 修改

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312214243885.png)

### 修改动态字段

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312220643910.png)

## 删除

### 删除一个

![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312221809878.png)

### 批量删除

批量就相当于多选，然后一次性修改，简单的思路就是把选取的id封装成一个数组，在sql语句里面吧这些id都删除

![image-20240312222701863](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312222701863.png)

其中问号的个数需要随着数组的大小变化而变化，mybatis会将传入的数组封装成一个map集合 ，key的默认名称是array

![image-20240312222942172](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240312222942172.png)

## MyBatis参数传递

![image-20240313175055929](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240313175055929.png)

![image-20240313181051228](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240313181051228.png)

@Param注解会将mybatis的默认参数名替换成括号内部的替换注解 ，开发的时候统一使用@Param注解替换参数名



对单个参数的封装

![image-20240313181634619](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240313181634619.png)

![ ](/Users/xiechen/Library/Application Support/typora-user-images/image-20240313181714282.png) 

思考题

![image-20240313181910748](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240313181910748.png)

## 注解开发案例（适合简单功能的实现）

 

## HTML&CSS

**今日目标：**

> * 能够掌握课程中讲解的标签的使用
> * 了解css的使用

## 1，HTML

### 1.1  介绍



==HTML(HyperText Markup Language)：超文本标记语言：==

* 超文本：超越了文本的限制，比普通文本更强大。除了文字信息，还可以定义图片、音频、视频等内容

  如上图看到的页面，我们除了能看到一些文字，同时也有大量的图片展示；有些网页也有视频，音频等。这种展示效果超越了文本展示的限制。

* 标记语言：由标签构成的语言

  之前学习的XML就是标记语言，由一个一个的标签组成，HTML 也是由标签组成 。我们在浏览器页面右键可以查看页面的源代码，如下

  ![image-20210811152519471](/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/html css/assets/image-20210811152519471.png)

  可以看到如下内容，就是由一个一个的标签组成的

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/html css/assets/image-20210811152558939.png" alt="image-20210811152558939" style="zoom:80%;" />

这些标签不像XML那样可以自定义，==HTML中的标签都是预定义好的，运行在浏览器上并由浏览器解析，==然后展示出对应的效果。例如我们想在浏览器上展示出图片就需要使用预定义的 `img` 标签；想展示可以点击的链接的效果就可以使用预定义的 `a` 标签等。

HTML 预定义了很多标签，由于我们是Java工程师、是做后端开发，所以不会每个都学习，页面开发是有专门的前端工程来开发。那为什么我们还要学习呢？在公司中或多或少大家也会涉及到前端开发。

简单的给大家聊一下开发流程：

以后我们是通过Java程序从数据库中查询出来数据，然后交给页面进行展示，这样用户就能通过在浏览器通过页面看到数据。

==W3C标准：==

W3C是万维网联盟，这个组成是用来定义标准的。他们规定了一个网页是由三部分组成，分别是：

* 结构：对应的是 HTML 语言
* 表现：对应的是 CSS 语言
* 行为：对应的是 JavaScript 语言

HTML定义页面的整体结构；CSS是用来美化页面，让页面看起来更加美观；JavaScript可以使网页动起来，比如轮播图也就是多张图片自动的进行切换等效果。

为了更好的给大家表述这三种语言的作用。我们通过具体的页面给大家说明。

如下只是使用HTML语言编写的页面的结构：

![image-20210811155026210](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811155026210.png)

可以看到页面是比较丑的，但是每一部分其实都已经包含了。接下来咱们加上 CSS 进行美化看到的效果如下：

![image-20210811155211181](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811155211181.png)

瞬间感觉好看多了，这就是CSS的作用，用来美化页面的。接下来再加上JavaScript试试

![image-20210811155404506](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811155404506.png)

在上图中可以看到多了轮播图，在浏览器上它是会自动切换图片的，并且切换的动态效果是很不错的。

看到了前端编写的这三个技术效果后，我们今天学习的是HTML，学习HTML其实就是学习预定义的这些标签。

### 1.2  快速入门

需求：编写如下图效果的页面

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811160100054.png" alt="image-20210811160100054" style="zoom:80%;" />

要实现这个页面，我们需要从以下三步进行实现

* 新建文本文件，后缀名改为 .html

  页面文件的后缀名是 .html，所以需要该后缀名

* 编写 HTML 结构标签

  HTML 是由一个一个的标签组成的，但是它也用于表示结构的标签

  ```html
  <html>
  	<head>
      	<title> </title>
      </head>
      <body>
          
      </body>
  </html>
  ```

  html标签是根标签，下面有 `head` 标签和 `body` 标签这两个子标签。而 `head` 标签的 `title` 子标签是用来定义页面标题名称的，它定义的内容会展示在浏览器的标题位置，如下图红框标记

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811160719292.png" alt="image-20210811160719292" style="zoom:80%;" />

  `body` 标签的内容会被展示在内容区中，如下图红框标记

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811160839423.png" alt="image-20210811160839423" style="zoom:80%;" />

  

* 在<body>中定义文字

代码如下：

```html
<html>
	<head>
    	<title>html 快速入门</title>
    </head>
    <body>
        乾坤未定，你我皆是黑马~
    </body>
</html>
```

同学们在访问其他网站页面时会看到字体颜色是五颜六色的，我们可以该字体颜色吗？当然可以了

`font` 标签就可以使用，该标签有一个 `color` 属性可以设置字体颜色，如： <font color='red'></font> 就是将文字设置成了红颜色。那么我们只需要将需要变成红色的文字放在标签体部分就可以了，如下：

```html
<html>
	<head>
    	<title>html 快速入门</title>
    </head>
    <body>
        <font color='red'>乾坤未定，你我皆是黑马~</font>
    </body>
</html>
```

==总结：==

* HTML 文件以.htm或.html为扩展名

* HTML 结构标签

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811161810610.png" alt="image-20210811161810610" style="zoom:70%;" />

* HTML 标签不区分大小写

  如上案例中的 `font` 写成 `Font` 也是一样可以展示出对应的效果的。

* HTML 标签属性值 单双引皆可

  如上案例中的color属性值使用双引号也是可以的。<font color="red"></font> 

* HTML 语法松散

  比如 font 标签不加结束标签也是可以展示出效果的。但是建议同学们在写的时候还是不要这样做，严格按照要求去写。



### 1.3  基础标签

基础标签就是一些和文字相关的标签，如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811171740881.png" alt="image-20210811171740881" style="zoom:80%;" />

接下来我们挨个进行讲解

#### 1.3.1  标题标签

* 创建模块

  在 Idea 中创建模块，而我们现在不需要写java代码，所以 `src` 目录就可以删除掉。在模块下创建一个html文件夹，该我们今天的所以的页面文件所部放在该文件夹下。模块目录如下

  ![image-20210811172254664](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811172254664.png)

* 创建页面文件

  选中 `html` 文件夹右键创建页面文件（01-基础标签.html）

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811172511287.png" alt="image-20210811172511287" style="zoom:80%;" />

  创建好后 idea 会自动加上结构标签，如下

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811172704525.png" alt="image-20210811172704525" style="zoom:80%;" />

  我们只需要在 `body` 标签中书写标签。

* 书写标题标签

  标题标签中 h1最大，h6最小。

  ```html
  <h1>我是标题 h1</h1>
  <h2>我是标题 h2</h2>
  <h3>我是标题 h3</h3>
  <h4>我是标题 h4</h4>
  <h5>我是标题 h5</h5>
  <h6>我是标题 h6</h6>
  ```

* 通过浏览器查看效果

  idea 提供了快捷的打开方式，如下图

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811172942861.png" alt="image-20210811172942861" style="zoom:80%;" />

  浏览器展示效果如下：

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811173034453.png" alt="image-20210811173034453" style="zoom:80%;" />

#### 1.3.2  hr标签

`hr` 标签在浏览器中呈现出 横线 的效果。

在页面文件中书写 hr 标签

```
<hr>
```

效果如下：

![image-20210811173605496](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811173605496.png)



#### 1.3.3  字体标签

font：字体标签

* face 属性：用来设置字体。如 "楷体"、"宋体"等

* color 属性：设置文字颜色。颜色有三种表示方式

  * **英文单词**：red,pink,blue...

    这种方式表示的颜色特别有限，所以一般不用。

  * **rgb(值1,值2,值3)**：值的取值范围：0~255  

    此种方式也就是三原色（红绿蓝）设置方式。 例如： rgb(255,0,0)。

    这种书写起来比较麻烦，一般不用。

  * **#值1值2值3**：值的范围：00~FF

    这种方式是rgb方式的简化写法，以后基本都用此方式。

    值1表示红色的范围，值2表示绿色的范围，值3表示蓝色范围。例如： #ff0000

* size 属性：设置文字大小

代码演示：

```html
<font face="楷体" size="5" color="#ff0000">传智教育</font>
```

效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811175246763.png" alt="image-20210811175246763" style="zoom:80%;" /> 

> ==注意：==
>
> font 标签已经不建议使用了，以后如果要改变文字字体，大小，颜色可以使用 CSS 进行设置。

#### 1.3.4  换行标签

在页面文件中书写如下内容

```
刚察草原绿草如茵，沙柳河水流淌入湖。藏族牧民索南才让家中，茶几上摆着馓子、麻花和水果，炉子上刚煮开的奶茶香气四溢……

6月8日下午，习近平总书记来到青海省海北藏族自治州刚察县沙柳河镇果洛藏贡麻村，走进牧民索南才让家中，看望慰问藏族群众。
```

 在浏览器展示的效果如下：

![image-20210811175442896](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811175442896.png)

我们可以看到并没有换行。如果要实现换行效果，需要使用 换行标签（br标签）。

修改页面文件内容如下：

```
刚察草原绿草如茵，沙柳河水流淌入湖。藏族牧民索南才让家中，茶几上摆着馓子、麻花和水果，炉子上刚煮开的奶茶香气四溢……<br>

6月8日下午，习近平总书记来到青海省海北藏族自治州刚察县沙柳河镇果洛藏贡麻村，走进牧民索南才让家中，看望慰问藏族群众。
```

浏览器打开效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811175649409.png" alt="image-20210811175649409" style="zoom:80%;" />

现在就有换行效果了。

#### 1.3.5  段落标签

上面文字展示的效果还是不太好，我们想让每一段上下都加空行。此时就需要使用段落标签（p标签）

在页面文件中书写如下内容：

```html
<p>
刚察草原绿草如茵，沙柳河水流淌入湖。藏族牧民索南才让家中，茶几上摆着馓子、麻花和水果，炉子上刚煮开的奶茶香气四溢……
</p>
<p>
6月8日下午，习近平总书记来到青海省海北藏族自治州刚察县沙柳河镇果洛藏贡麻村，走进牧民索南才让家中，看望慰问藏族群众。
</p>
```

在浏览器展示的效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811180041023.png" alt="image-20210811180041023" style="zoom:80%;" />

这种效果就会比之前的效果好一些，呈现出段落的效果。

#### 1.3.6  加粗、斜体、下划线标签

* b：加粗标签
* i：斜体标签
* u：下划线标签，在文字的下方有一条横线

代码如下：

```html
<b>沙柳河水流淌</b><br>
<i>沙柳河水流淌</i><br>
<u>沙柳河水流淌</u><br>
```

在浏览器展示的效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811180336928.png" alt="image-20210811180336928" style="zoom:80%;" />

#### 1.3.7  居中标签

center ：文本居中

代码如下：

```html
<hr>
<center>
    <b>沙柳河水流淌</b>
</center>
```

在浏览器效果如下：

![image-20210811180702247](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811180702247.png)

#### 1.3.8  案例

实现如下图所示页面效果：

![image-20210811180755814](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811180755814.png)

此案例同学们自己实现，用我们学过的基础标签。

> 注意：在上图页面中版权所有里有特殊字符，需要使用转义字符。有如下转义字符：
>
> <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811180929858.png" alt="image-20210811180929858" style="zoom:70%;" /> 

### 1.4  图片、音频、视频标签

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811181303117.png" alt="image-20210811181303117" style="zoom:70%;" />

* img：定义图片

  * src：规定显示图像的 URL（统一资源定位符）

  * height：定义图像的高度

  * width：定义图像的宽度

* audio：定义音频。支持的音频格式：MP3、WAV、OGG 

  * src：规定音频的 URL

  * controls：显示播放控件

* video：定义视频。支持的音频格式：MP4, WebM、OGG
  * src：规定视频的 URL
  * controls：显示播放控件

**尺寸单位：**

height属性和width属性有两种设置方式：

* 像素：单位是px
* 百分比。占父标签的百分比。例如宽度设置为 50%，意思就是占它的父标签宽度的一般（50%）

**资源路径：**

图片，音频，视频标签都有src属性，而src是用来指定对应的图片，音频，视频文件的路径。此处的图片，音频，视频就称为资源。资源路径有如下两种设置方式：

* 绝对路径：完整路径

  这里的绝对路径是网络中的绝对路径。 格式为： 协议://ip地址:端口号/资源名称。

  如：

  ```
  <img src="https://th.bing.com/th/id/R33674725d9ae34f86e3835ae30b20afe?rik=Pb3C9e5%2b%2b3a9Vw&riu=http%3a%2f%2fwww.desktx.com%2fd%2ffile%2fwallpaper%2fscenery%2f20180626%2f4c8157d07c14a30fd76f9bc110b1314e.jpg&ehk=9tpmnrrRNi0eBGq3CnhwvuU8PPmKuy1Yma0zL%2ba14T0%3d&risl=&pid=ImgRaw" width="300" height="400">
  ```

  这里src属性的值就是网络中的绝对路径。

* 相对路径：相对位置关系

  找页面和其他资源的相对路径。

  > ./    表示当前路径
  >
  > ../   表示上一级路径
  >
  > ../../   表示上两级路径

  如模块目录结构如下：

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811190840184.png" alt="image-20210811190840184" style="zoom:80%;" />

  在 `01-基础标签.html` 里的标签中找不同的图片，路径写法不同

  ```html
  <!--在该页面找a.jpg，就需要先回到上一级目录，该级目录有img目录，进入该目录就可以找到 a.jpg图片-->
  <img src="../img/a.jpg" width="300" height="400">
  <!--该页面和aa.jpg 是在同一级下，所以可以直接写 图片的名称，也可以写成  ./aa.jpg-->
  <img src="aa.jpg" width="300" height="400">
  ```

使用这些标签的代码如下：

```html
<img src="../img/a.jpg" width="300" height="400">
<audio src="b.mp3" controls></audio>
<video src="c.mp4" controls width="500" height="300"></video>
```

在浏览器展示的效果如下：

![image-20210811191514642](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811191514642.png)

### 1.5  超链接标签

在网页中可以看到很多超链接标签，如下

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811191725308.png" alt="image-20210811191725308" style="zoom:80%;" />

上图红框中的都是超链接，当我们点击这些超链接时会跳转到其他的页面或者资源。而超链接使用的是 `a` 标签。

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811191852726.png" alt="image-20210811191852726" style="zoom:70%;" />

`a` 标签属性：

* href：指定访问资源的URL 

* target：指定打开资源的方式
  * _self：默认值，在当前页面打开
  * _blank：在空白页面打开

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
	<a href="https://www.itcast.cn" target="_self">点我有惊喜</a>
</body>
</html>
```

效果图示：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811192332854.png" alt="image-20210811192332854" style="zoom:70%;" />

当我们将 `target` 属性值设置为 `_blank`，效果图示：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811192512960.png" alt="image-20210811192512960" style="zoom:70%;" />

### 1.6  列表标签

HTML 中列表分为

* 有序列表

  如下图，页面效果中是有标号对每一项进行标记的。

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811192825145.png" alt="image-20210811192825145" style="zoom:80%;" />

* 无序列表

  如下图，页面效果中没有标号对每一项进行标记，而是使用 点 进行标记。

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811192905834.png" alt="image-20210811192905834" style="zoom:80%;" />

**标签说明：**

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811193105881.png" alt="image-20210811193105881" style="zoom:60%;" />

有序列表中的 `type` 属性用来指定标记的标号的类型（数字、字母、罗马数字等）

无序列表中的 `type` 属性用来指定标记的形状

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <ol type="A">
        <li>咖啡</li>
        <li>茶</li>
        <li>牛奶</li>
    </ol>
    
    <ul type="circle">
        <li>咖啡</li>
        <li>茶</li>
        <li>牛奶</li>
    </ul>
</body>
</html>
```

### 1.7  表格标签

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811193819851.png" alt="image-20210811193819851" style="zoom:80%;" />

如上图就是一个表格，表格可以使用如下标签定义

* table ：定义表格

  * border：规定表格边框的宽度

  * width ：规定表格的宽度

  * cellspacing：规定单元格之间的空白

* tr ：定义行

  * align：定义表格行的内容对齐方式

* td ：定义单元格

  * rowspan:规定单元格可横跨的行数

  * colspan:规定单元格可横跨的列数

* th：定义表头单元格

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<table border="1" cellspacing="0" width="500">
    <tr>
        <th>序号</th>
        <th>品牌logo</th>
        <th>品牌名称</th>
        <th>企业名称</th>   
    </tr>
    <tr align="center">
        <td>010</td>
        <td><img src="../img/三只松鼠.png" width="60" height="50"></td>
        <td>三只松鼠</td>
        <td>三只松鼠</td>
    </tr>

    <tr align="center">
        <td>009</td>
        <td><img src="../img/优衣库.png" width="60" height="50"></td>
        <td>优衣库</td>
        <td>优衣库</td>
    </tr>

    <tr align="center">
        <td>008</td>
        <td><img src="../img/小米.png" width="60" height="50"></td>
        <td>小米</td>
        <td>小米科技有限公司</td>
    </tr>
</table>
</body>
</html>
```

### 1.8  布局标签

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811194410699.png" alt="image-20210811194410699" style="zoom:80%;" />

这两个标签，一般都是和css结合到一块使用来实现页面的布局。

`div`标签 在浏览器上会有换行的效果，而 `span` 标签在浏览器上没有换行效果。

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div>我是div</div>
    <div>我是div</div>
    <span>我是span</span>
    <span>我是span</span>
</body>
</html>
```

**浏览器效果如下：**

![image-20210811194739313](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210811194739313.png)

### 1.9  表单标签

表单标签效果大家其实都不陌生，像登陆页面、注册页面等都是表单。

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812215311168.png" alt="image-20210812215311168" style="zoom:80%;" />

像这样的表单就是用来采集用户输入的数据，然后将数据发送到服务端，服务端会对数据库进行操作，比如注册就是将数据保存到数据库中，而登陆就是根据用户名和密码进行数据库的查询操作。

表单是很重要的标签，需要大家重点来学习。

#### 1.9.1  表单标签概述

> 表单：在网页中主要负责数据采集功能，使用<form>标签定义表单
>
> 表单项(元素)：不同类型的 input 元素、下拉列表、文本域等

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812215704511.png" alt="image-20210812215704511" style="zoom:80%;" />

`form` 是表单标签，它在页面上没有任何展示的效果。需要借助于表单项标签来展示不同的效果。如下图就是不同的表单项标签展示出来的效果。

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812215857298.png" alt="image-20210812215857298" style="zoom:70%;" />

#### 1.9.2  form标签属性

* **action：规定当提交表单时向何处发送表单数据，该属性值就是URL**

  以后会将数据提交到服务端，该属性需要书写服务端的URL。而今天我们可以书写 `#` ，表示提交到当前页面来看效果。

* **method ：规定用于发送表单数据的方式**

  method取值有如下两种：

  * get：默认值。如果不设置method属性则默认就是该值
    * 请求参数会拼接在URL后边
    * url的长度有限制 4KB
  * post：
    * 浏览器会将数据放到http请求消息体中
    * 请求参数无限制的

#### 1.9.3  代码演示

由于表单标签在页面上没有任何展示的效果，所以在演示的过程是会先使用 `input` 这个表单项标签展示输入框效果。

代码如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <form>
        <input type="text">
        <input type="submit">
    </form>
</body>
</html>
```

浏览器展示效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812220926114.png" alt="image-20210812220926114" style="zoom:90%;" /> 

从效果可以看到页面有一个输入框，用户可以在数据框中输入自己想输入的内容，点击提交按钮以后会将数据发送到服务端，当然现在肯定不能实现。现在我们可以将 `form` 标签的 `action` 属性值设置为 `#` ，将其将数据提交到当前页面。还需要注意一点，要想提交数据，`input` 输入框必须设置 `name` 属性。代码如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <form action="#">
        <input type="text" name="username">
        <input type="submit">
    </form>
</body>
</html>
```

浏览器展示效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812221656295.png" alt="image-20210812221656295" style="zoom:80%;" /> 

在输入框输入 `hehe` ，然后点击 `提交` 按钮，就能看到如下效果

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812221801965.png" alt="image-20210812221801965" style="zoom:80%;" /> 

我们可以看到在浏览器的地址栏的URL后拼接了我们提交的数据。`username` 就是输入框 `name` 属性值，而 `hehe` 就是我们在输入框输入的内容。

接下来我们来聊 `method` 属性，默认是 `method = 'get'`，所以该取值就会将数据拼接到URL的后面。那我们将 `method` 属性值设置为 `post`，浏览器的效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812222334790.png" alt="image-20210812222334790" style="zoom:80%;" /> 

从上图可以看出数据并没有拼接到 URL 后，那怎么看提交的数据呢？我们可以使用浏览器的开发者工具来查看

![image-20210812222623912](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812222623912.png)

按照如上步骤操作能看到如下页面

![image-20210812223004607](/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/html css/assets/image-20210812223004607.png)

重新提交数据后，可以看到提交的数据，如下图

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812223150373.png" alt="image-20210812223150373" style="zoom:80%;" />

### 1.10  表单项标签

表单项标签有很多，不同的表单项标签有不同的展示效果。表单项标签可以分为以下三个：

* \<input>：表单项，通过type属性控制输入形式

  `input` 标签有个 `type` 属性。 `type` 属性的取值不同，展示的效果也不一样

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812223956360.png" alt="image-20210812223956360" style="zoom:80%;" />

  

* \<select>：定义下拉列表，\<option> 定义列表项 

  如下图就是下拉列表的效果：

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812223708205.png" alt="image-20210812223708205" style="zoom:80%;" /> 

* \<textarea>：文本域

  如下图就是文本域效果。它可以输入多行文本，而 `input` 数据框只能输入一行文本。

  ![image-20210812223744522](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812223744522.png) 

> ==注意：==
>
> * 以上标签项的内容要想提交，必须得定义 `name` 属性。
> * 每一个标签都有id属性，id属性值是唯一的标识。
> * 单选框、复选框、下拉列表需要使用 `value` 属性指定提交的值。

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <form action="#" method="post">
        <input type="hidden" name="id" value="123">

        <label for="username">用户名：</label>
        <input type="text" name="username" id="username"><br>

        <label for="password">密码：</label>
        <input type="password" name="password" id="password"><br>

        性别：
        <input type="radio" name="gender" value="1" id="male"> <label for="male">男</label>
        <input type="radio" name="gender" value="2" id="female"> <label for="female">女</label>
        <br>

        爱好：
        <input type="checkbox" name="hobby" value="1"> 旅游
        <input type="checkbox" name="hobby" value="2"> 电影
        <input type="checkbox" name="hobby" value="3"> 游戏
        <br>

        头像：
        <input type="file"><br>

        城市:
        <select name="city">
            <option>北京</option>
            <option value="shanghai">上海</option>
            <option>广州</option>
        </select>
        <br>

        个人描述：
        <textarea cols="20" rows="5" name="desc"></textarea>
        <br>
        <br>
        <input type="submit" value="免费注册">
        <input type="reset" value="重置">
        <input type="button" value="一个按钮">
    </form>
</body>
</html>
```

在浏览器的效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812224152747.png" alt="image-20210812224152747" style="zoom:80%;" />

## 2，CSS

### 2.1  概述

==CSS 是一门语言，用于控制网页表现。==我们之前介绍过W3C标准。W3C标准规定了网页是由以下组成：

* 结构：HTML
* 表现：CSS
* 行为：JavaScript

CSS也有一个专业的名字：==Cascading Style Sheet（层叠样式表）。==

如下面的代码， `style` 标签中定义的就是css代码。该代码描述了将 div 标签的内容的字体颜色设置为 红色。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            color: red;
        }
    </style>
</head>
<body>
    <div>Hello CSS~</div>
</body>
</html>
```

在浏览器中的效果如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812225424174.png" alt="image-20210812225424174" style="zoom:60%;" />

### 2.2  css 导入方式

css 导入方式其实就是 css 代码和 html 代码的结合方式。CSS 导入 HTML有三种方式：

* 内联样式：在标签内部使用style属性，属性值是css属性键值对

  ```html
  <div style="color: red">Hello CSS~</div>
  ```

  > 给方式只能作用在这一个标签上，如果其他的标签也想使用同样的样式，那就需要在其他标签上写上相同的样式。复用性太差。

* 内部样式：定义<style>标签，在标签内部定义css样式

  ```html
  <style type="text/css">
  	div{
  		color: red;
      }
  </style>
  ```

  > 这种方式可以做到在该页面中复用。

* 外部样式：定义link标签，引入外部的css文件

  编写一个css文件。名为：demo.css，内容如下:

  ```css
  div{
  	color: red;
  }
  ```

  在html中引入 css 文件。

  ```html
  <link rel="stylesheet"  href="demo.css">
  ```

  > 这种方式可以在多个页面进行复用。其他的页面想使用同样的样式，只需要使用 `link` 标签引入该css文件。

**代码演示：**

项目目录结构如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812231514311.png" alt="image-20210812231514311" style="zoom:80%;" />

编写页面 `02-导入方式.html`，内容如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        span{
            color: red;
        }
    </style>
    <link href="../css/demo.css" rel="stylesheet">
</head>
<body>
    <div style="color: red">hello css</div>

    <span>hello css </span>

    <p>hello css</p>
</body>
</html>
```

### 2.3  css 选择器

css 选择器就是选取需设置样式的元素（标签），比如如下css代码：

```css
div {
	color:red;
}
```

如上代码中的 `div` 就是 css 中的选择器。我们只讲下面三种选择器：

* 元素选择器

  格式：

  ```css
  元素名称{color: red;}
  ```

  例子：

  ```
  div {color:red}  /*该代码表示将页面中所有的div标签的内容的颜色设置为红色*/
  ```

* id选择器

  需要制定特别的形式就用id选择，元素直接吧所有的都选择上去了

  格式：

  ```css
  #id属性值{color: red;}
  ```

  例子：

  html代码如下：

  ```html
  <div id="name">hello css2</div>
  ```

  css代码如下：

  ```css
  #name{color: red;}/*该代码表示将页面中所有的id属性值是 name 的标签的内容的颜色设置为红色*/
  ```

* 类选择器

  格式：

  ```css
  .class属性值{color: red;}
  ```

  例子：

  html代码如下：

  ```html
  <div class="cls">hello css3</div>
  ```

  css代码如下：

  ```css
  .cls{color: red;} /*该代码表示将页面中所有的class属性值是 cls 的标签的内容的颜色设置为红色*/
  ```

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        div{
            color: red;
        }

        #name{
            color: blue;
        }

        .cls{
            color: pink;
        }
    </style>

</head>
<body>
    <div>div1</div>
    <div id="name">div2</div>
    <div class="cls">div3</div>
    <span class="cls">span</span>
</body>
</html>
```



### 2.4  css 属性

css属性我们不作为重点讲解。我们简单的看一下css的文档

![image-20210812233107495](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812233107495.png)

css有很多css属性，你要想把它们都学会，需要花费很长的时间。而我们作为java程序员，不需要重点掌握这部分内容。对于网页三剑客中css是对我们要求最低的。给大家简单介绍一下文档怎么查看即可，如下我们看一个 `background-color` 属性

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812233415060.png" alt="image-20210812233415060" style="zoom:80%;" />

点击进去后能看到下面界面

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210812233510734.png" alt="image-20210812233510734" style="zoom:70%;" />

上面就列举了该属性的具体的使用，你也可以点击下面的 `亲自试一试` 看效果。

## JavaScript

**今日目标**

> * 掌握 JavaScript 的基础语法
> * 掌握 JavaScript 的常用对象（Array、String）
> * 能根据需求灵活运用定时器及通过 js 代码进行页面跳转
> * 能通过DOM 对象对标签进行常规操作
> * 掌握常用的事件
> * 能独立完成表单校验案例

## 1，JavaScript简介

==JavaScript 是一门跨平台、面向对象的脚本语言==，而Java语言也是跨平台的、面向对象的语言，只不过Java是编译语言，是需要编译成字节码文件才能运行的；JavaScript是脚本语言，不需要编译，由浏览器直接解析并执行。

JavaScript 是用来控制网页行为的，它能使网页可交互；那么它可以做什么呢？如改变页面内容、修改指定元素的属性值、对表单进行校验等，下面是这些功能的效果展示：

* **改变页面内容**

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210814173417834.png" alt="image-20210814173417834" style="zoom:80%;" />

  当我点击上面左图的 `点击我` 按钮，按钮上面的文本就改为上面右图内容，这就是js 改变页面内容的功能。

* **修改指定元素的属性值**

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210814173719505.png" alt="image-20210814173719505" style="zoom:70%;" />

  当我们点击上图的 `开灯` 按钮，效果就是上面右图效果；当我点击 `关灯` 按钮，效果就是上面左图效果。其他这个功能中有两张灯泡的图片（使用img标签进行展示），通过修改 img 标签的 src 属性值改变展示的图片来实现。

* **对表单进行校验**

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210814174242688.png" alt="image-20210814174242688" style="zoom:70%;" />

  在上面左图的输入框输入用户名，如果输入的用户名是不满足规则的就展示右图(上) 的效果；如果输入的用户名是满足规则的就展示右图(下) 的效果。

JavaScript 和 Java 是完全不同的语言，不论是概念还是设计，只是名字比较像而已。但是==基础语法类似==，所以我们有java的学习经验，再学习JavaScript 语言就相对比较容易些。

JavaScript（简称：JS） 在 1995 年由 Brendan Eich 发明，并于 1997 年成为一部 ECMA 标准。ECMA 规定了一套标准 就叫 `ECMAScript` ，所有的客户端校验语言必须遵守这个标准，当然 JavaScript 也遵守了这个标准。ECMAScript 6 (简称ES6) 是最新的 JavaScript 版本（发布于 2015 年)，我们的课程就是基于最新的 `ES6` 进行讲解。

## 2，JavaScript引入方式

JavaScript 引入方式就是 HTML 和 JavaScript 的结合方式。JavaScript引入方式有两种：

* 内部脚本：将 JS代码定义在HTML页面中
* 外部脚本：将 JS代码定义在外部 JS文件中，然后引入到 HTML页面中

### 2.1  内部脚本

在 HTML 中，JavaScript 代码必须位于 `<script>` 与 `</script>` 标签之间

**代码如下：**

`alert(数据)` 是 JavaScript 的一个方法，作用是将参数数据以浏览器弹框的形式输出出来。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<script>
    alert("hello js1");
</script>
</body>
</html>
```

**效果如下：**

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210814181419691.png" alt="image-20210814181419691" style="zoom:70%;" />

从结果可以看到 js 代码已经执行了。

> ==提示：==
>
> * 在 HTML 文档中可以在任意地方，放置任意数量的<script>标签。如下图
>
>   ```html
>   <!DOCTYPE html>
>   <html lang="en">
>   <head>
>       <meta charset="UTF-8">
>       <title>Title</title>
>       <script>
>           alert("hello js1");
>       </script>
>   </head>
>   <body>
>   
>   <script>
>       alert("hello js1");
>   </script>
>   
>   </body>
>   </html>
>   <script>
>       alert("hello js1");
>   </script>
>   ```
>
> * 一般把脚本置于 <body> 元素的底部，可改善显示速度
>
>   因为浏览器在加载页面的时候会从上往下进行加载并解析。 我们应该让用户看到页面内容，然后再展示动态的效果。

### 2.2  外部脚本

**第一步：定义外部 js 文件。如定义名为 demo.js的文件**

项目结构如下：

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210814182345236.png" alt="image-20210814182345236" style="zoom:80%;" />

demo.js 文件内容如下：

```js
alert("hello js");
```

**第二步：在页面中引入外部的js文件**

在页面使用 `script` 标签中使用 `src` 属性指定 js 文件的 URL 路径。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<script src="../js/demo.js"></script>
</body>
</html>
```

> ==注意：==
>
> * 外部脚本不能包含 `<script>` 标签
>
>   在js文件中直接写 js 代码即可，不要在 js文件 中写 `script` 标签
>
> * `<script>` 标签不能自闭合
>
>   在页面中引入外部js文件时，不能写成 `<script src="../js/demo.js" />`。

## 3，JavaScript基础语法

### 3.1  书写语法

* 区分大小写：与 Java 一样，变量名、函数名以及其他一切东西都是区分大小写的

* 每行结尾的分号可有可无

  如果一行上写多个语句时，必须加分号用来区分多个语句。

* 注释

  * 单行注释：// 注释内容
  * 多行注释：/* 注释内容 */

  > 注意：JavaScript 没有文档注释

* 大括号表示代码块

  下面语句大家肯定能看懂，和 java 一样 大括号表示代码块。

  ```js
  if (count == 3) { 
     alert(count); 
  } 
  ```

### 3.2  输出语句

js 可以通过以下方式进行内容的输出，只不过不同的语句输出到的位置不同

* **使用 window.alert() 写入警告框**

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
      
  <script>
      window.alert("hello js");//写入警告框
  </script>
  </body>
  </html>
  ```

  上面代码通过浏览器打开，我们可以看到如下图弹框效果

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210814181419691.png" alt="image-20210814181419691" style="zoom:70%;" />

* **使用 document.write() 写入 HTML 输出**

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
      
  <script>
      document.write("hello js 2~");//写入html页面
  </script>
  </body>
  </html>
  ```

  上面代码通过浏览器打开，我们可以在页面上看到 `document.write(内容)` 输出的内容

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210814190302845.png" alt="image-20210814190302845" style="zoom:80%;" />

* **使用 console.log() 写入浏览器控制台**

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <script>
      console.log("hello js 3");//写入浏览器的控制台
  </script>
  </body>
  </html>
  ```

  上面代码通过浏览器打开，我们可以在不能页面上看到  `console.log(内容)` 输出的内容，它是输出在控制台了，而怎么在控制台查看输出的内容呢？在浏览器界面按 `F12` 就可以看到下图的控制台

  ![image-20210814190906202](/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210814190906202.png)

### 3.3  变量

JavaScript 中用 var 关键字（variable 的缩写）来声明变量。格式 `var 变量名 = 数据值;`。而在JavaScript 是一门弱类型语言，变量==可以存放不同类型的值==；如下在定义变量时赋值为数字数据，还可以将变量的值改为字符串类型的数

```js
var test = 20;
test = "张三";
```

js 中的变量名命名也有如下规则，和java语言基本都相同

* 组成字符可以是任何字母、数字、下划线（_）或美元符号（$）
* 数字不能开头
* 建议使用驼峰命名

JavaScript 中 `var` 关键字有点特殊，有以下地方和其他语言不一样

* 作用域：全局变量

  ```js
  {
      var age = 20;
  }
  alert(age);  // 在代码块中定义的age 变量，在代码块外边还可以使用
  ```

* 变量可以重复定义

  ```js
  {
      var age = 20;
      var age = 30;//JavaScript 会用 30 将之前 age 变量的 20 替换掉
  }
  alert(age); //打印的结果是 30
  ```

针对如上的问题，==ECMAScript 6 新增了 `let `关键字来定义变量。==它的用法类似于 `var`，但是所声明的变量，只在 `let` 关键字所在的代码块内有效，且不允许重复声明。

例如：

```js
{
    let age = 20;
}
alert(age); 
```

运行上面代码，浏览器并没有弹框输出结果，说明这段代码是有问题的。通过 `F12` 打开开发者模式可以看到如下错误信息

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815170848426.png" alt="image-20210815170848426" style="zoom:80%;" />

而如果在代码块中定义两个同名的变量，IDEA 开发工具就直接报错了

> <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815170952829.png" alt="image-20210815170952829" style="zoom:80%;" />

==ECMAScript 6 新增了 const关键字，用来声明一个只读的常量。一旦声明，常量的值就不能改变。== 通过下面的代码看一下常用的特点就可以了

> <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815171128095.png" alt="image-20210815171128095" style="zoom:80%;" />

我们可以看到给 PI 这个常量重新赋值时报错了。

### 3.4  数据类型

JavaScript 中提供了两类数据类型：原始类型 和 引用类型。

> 使用 typeof 运算符可以获取数据类型
>
> `alert(typeof age);` 以弹框的形式将 age 变量的数据类型输出

原始数据类型：

* **number**：数字（整数、小数、NaN(Not a Number)）

  ```js
  var age = 20;
  var price = 99.8;
  
  alert(typeof age); // 结果是 ： number
  alert(typeof price);// 结果是 ： number
  ```

  > ==注意：== NaN是一个特殊的number类型的值，后面用到再说

* **string**：字符、字符串，单双引皆可

  ```js
  var ch = 'a';
  var name = '张三'; 
  var addr = "北京";
  
  alert(typeof ch); //结果是  string
  alert(typeof name); //结果是  string
  alert(typeof addr); //结果是  string
  ```

  > ==注意：==在 js 中 双引号和单引号都表示字符串类型的数据

* **boolean**：布尔。true，false

  ```js
  var flag = true;
  var flag2 = false;
  
  alert(typeof flag); //结果是 boolean
  alert(typeof flag2); //结果是 boolean
  ```

* **null**：对象为空

  ```js
  var obj = null;
  
  alert(typeof obj);//结果是 object
  ```

  为什么打印上面的 obj 变量的数据类型，结果是object；这个官方给出了解释，下面是从官方文档截的图

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815173003408.png" alt="image-20210815173003408" style="zoom:80%;" />

* **undefined**：当声明的变量未初始化时，该变量的默认值是 undefined

  ```js
  var a ;
  alert(typeof a); //结果是 undefined
  ```

### 3.5  运算符

JavaScript 提供了如下的运算符。大部分和 Java语言 都是一样的，不同的是 JS 关系运算符中的 `==` 和 `===`，一会我们只演示这两个的区别，其他运算符将不做演示

* 一元运算符：++，--

* 算术运算符：+，-，*，/，%

* 赋值运算符：=，+=，-=…

* 关系运算符：>，<，>=，<=，!=，\==，===…

* 逻辑运算符：&&，||，!

* 三元运算符：条件表达式 ? true_value : false_value 

#### 3.5.1  \==和===区别

**概述:**

* ==：

  1. 判断类型是否一样，如果不一样，则进行类型转换

  2. 再去比较其值

* ===：js 中的全等于

  1. 判断类型是否一样，如果不一样，直接返回false
  2. 再去比较其值

**代码：**

```js
var age1 = 20;
var age2 = "20";

alert(age1 == age2);// true
alert(age1 === age2);// false
```

#### 3.5.2  类型转换

上述讲解 `==` 运算符时，发现会进行类型转换，所以接下来我们来详细的讲解一下 JavaScript 中的类型转换。

* 其他类型转为number

  * string 转换为 number 类型：按照字符串的字面值，转为数字。如果字面值不是数字，则转为NaN

    将 string 转换为 number 有两种方式：

    * 使用 `+` 正号运算符：

      ```js
      var str = +"20";
      alert(str + 1) //21
      ```

    * 使用 `parseInt()` 函数(方法)：

      ```js
      var str = "20";
      alert(parseInt(str) + 1);
      ```

    > ==建议使用 `parseInt()` 函数进行转换。==

  * boolean 转换为 number 类型：true 转为1，false转为0

    ```js
    var flag = +false;
    alert(flag); // 0
    ```

* 其他类型转为boolean

  * number 类型转换为 boolean 类型：0和NaN转为false，其他的数字转为true
  * string 类型转换为 boolean 类型：空字符串转为false，其他的字符串转为true
  * null类型转换为 boolean 类型是 false
  * undefined 转换为 boolean 类型是 false

  **代码如下：**

  ```js
  // var flag = 3;
  // var flag = "";
  var flag = undefined;
  
  if(flag){
      alert("转为true");
  }else {
      alert("转为false");
  }
  ```

**使用场景：**

在 Java 中使用字符串前，一般都会先判断字符串不是null，并且不是空字符才会做其他的一些操作，JavaScript也有类型的操作，代码如下：

```js
var str = "abc";

//健壮性判断
if(str != null && str.length > 0){
    alert("转为true");
}else {
    alert("转为false");
}
```

但是由于 JavaScript 会自动进行类型转换，所以上述的判断可以进行简化，代码如下：

```js
var str = "abc";

//健壮性判断
if(str){
    alert("转为true");
}else {
    alert("转为false");
}
```



### 3.6  流程控制语句

JavaScript 中提供了和 Java 一样的流程控制语句，如下

* if 
* switch
* for
* while
* dowhile

#### 3.6.1  if 语句

```js
var count = 3;
if (count == 3) {
    alert(count);
}
```

#### 3.6.2  switch 语句

```js
var num = 3;
switch (num) {
    case 1:
        alert("星期一");
        break;
    case 2:
        alert("星期二");
        break;
    case 3:
        alert("星期三");
        break;
    case 4:
        alert("星期四");
        break;
    case 5:
        alert("星期五");
        break;
    case 6:
        alert("星期六");
        break;
    case 7:
        alert("星期日");
        break;
    default:
        alert("输入的星期有误");
        break;
}
```

#### 3.6.3  for 循环语句

```js
var sum = 0;
for (let i = 1; i <= 100; i++) { //建议for循环小括号中定义的变量使用let
    sum += i;
}
alert(sum);
```

#### 3.6.4  while 循环语句

```js
var sum = 0;
var i = 1;
while (i <= 100) {
    sum += i;
    i++;
}
alert(sum);
```

#### 3.6.5  dowhile 循环语句

```js
var sum = 0;
var i = 1;
do {
    sum += i;
    i++;
}
while (i <= 100);
alert(sum);
```

### 3.7  函数

函数（就是Java中的方法）是被设计为执行特定任务的代码块；JavaScript 函数通过 function 关键词进行定义。

#### 3.7.1  定义格式

函数定义格式有两种：

* 方式1

  ```js
  function 函数名(参数1,参数2..){
      要执行的代码
  }
  ```

* 方式2

  ```js
  var 函数名 = function (参数列表){
      要执行的代码
  }
  ```

> ==注意：==
>
> * 形式参数不需要类型。因为JavaScript是弱类型语言
>
>   ```js
>   function add(a, b){
>       return a + b;
>   }
>   ```
>
>   上述函数的参数 a 和 b 不需要定义数据类型，因为在每个参数前加上 var 也没有任何意义。
>
> * 返回值也不需要定义类型，可以在函数内部直接使用return返回即可

#### 3.7.2  函数调用

函数调用函数：

```js
函数名称(实际参数列表);
```

eg：

```js
let result = add(10,20);
```

> ==注意：==
>
> * JS中，函数调用可以传递任意个数参数
>
> * 例如  `let result = add(1,2,3);` 
>
>   它是将数据 1 传递给了变量a，将数据 2 传递给了变量 b，而数据 3 没有变量接收。

## 4，JavaScript常用对象

JavaScript 提供了很多对象供使用者来使用。这些对象总共分类三类

* 基本对象

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815183147297.png" alt="image-20210815183147297" style="zoom:80%;" />

* BOM 对象

  <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815183207660.png" alt="image-20210815183207660" style="zoom:80%;" />

* DOM对象

  DOM 中的对象就比较多了，下图只是截取部分

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815183225718.png" alt="image-20210815183225718" style="zoom:80%;" />

这小节我们先学习基本对象，而我们先学习 `Array` 数组对象和 `String` 字符串对象。

### 4.1  Array对象

JavaScript Array对象用于定义数组

#### 4.1.1  定义格式

数组的定义格式有两种：

* 方式1

  ```js
  var 变量名 = new Array(元素列表); 
  ```

  例如：

  ```js
  var arr = new Array(1,2,3); //1,2,3 是存储在数组中的数据（元素）
  ```

* 方式2

  ```js
  var 变量名 = [元素列表];
  ```

  例如：

  ```js
  var arr = [1,2,3]; //1,2,3 是存储在数组中的数据（元素）
  ```

  ==注意：Java中的数组静态初始化使用的是{}定义，而 JavaScript 中使用的是 [] 定义==

#### 4.1.2  元素访问

访问数组中的元素和 Java 语言的一样，格式如下：

```js
arr[索引] = 值;
```

**代码演示：**

```js
 // 方式一
var arr = new Array(1,2,3);
// alert(arr);

// 方式二
var arr2 = [1,2,3];
//alert(arr2);

// 访问
arr2[0] = 10;
alert(arr2)
```

#### 4.1.3  特点

JavaScript 中的数组相当于 Java 中集合。数组的长度是可以变化的，而 JavaScript 是弱类型，所以可以存储任意的类型的数据。

例如如下代码：

```js
// 变长
var arr3 = [1,2,3];
arr3[10] = 10;
alert(arr3[10]); // 10
alert(arr3[9]);  //undefined
```

上面代码在定义数组中给了三个元素，又给索引是 10 的位置添加了数据 10，那么 `索引3` 到 `索引9` 位置的元素是什么呢？我们之前就介绍了，在 JavaScript 中没有赋值的话，默认就是 `undefined`。

如果给 `arr3` 数组添加字符串的数据，也是可以添加成功的

```js
arr3[5] = "hello";
alert(arr3[5]); // hello
```

#### 4.1.4  属性

Array 对象提供了很多属性，如下图是官方文档截取的

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815190319166.png" alt="image-20210815190319166" style="zoom:80%;" />

而我们只讲解 `length` 属性，该数组可以动态的获取数组的长度。而有这个属性，我们就可以遍历数组了

```js
var arr = [1,2,3];
for (let i = 0; i < arr.length; i++) {
    alert(arr[i]);
}
```

#### 4.1.5  方法

Array 对象同样也提供了很多方法，如下图是官方文档截取的

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815190601340.png" alt="image-20210815190601340" style="zoom:80%;" />

而我们在课堂中只演示 `push` 函数和 `splice` 函数。

* push 函数：给数组添加元素，也就是在数组的末尾添加元素

  参数表示要添加的元素

  ```js
  // push:添加方法
  var arr5 = [1,2,3];
  arr5.push(10);
  alert(arr5);  //数组的元素是 {1,2,3,10}
  ```

* splice 函数：删除元素

  参数1：索引。表示从哪个索引位置删除

  参数2：个数。表示删除几个元素

  ```js
  // splice:删除元素
  var arr5 = [1,2,3];
  arr5.splice(0,1); //从 0 索引位置开始删除，删除一个元素 
  alert(arr5); // {2,3}
  ```

### 4.2  String对象

String对象的创建方式有两种

* 方式1：

  ```js
  var 变量名 = new String(s); 
  ```

* 方式2：

  ```js
  var 变量名 = "数组"; 
  ```

**属性：**

String对象提供了很多属性，下面给大家列举了一个属性 `length` ，该属性是用于动态的获取字符串的长度

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815192504884.png" alt="image-20210815192504884" style="zoom:60%;" />

**函数：**

String对象提供了很多函数（方法），下面给大家列举了两个方法。

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815192544172.png" alt="image-20210815192544172" style="zoom:70%;" />

String对象还有一个函数 `trim()` ，该方法在文档中没有体现，但是所有的浏览器都支持；它是用来去掉字符串两端的空格。

代码演示：

```js
var str4 = '  abc   ';
alert(1 + str4 + 1);
```

上面代码会输出内容 `1  abc  1`，很明显可以看到 abc 字符串左右两边是有空格的。接下来使用 `trim()` 函数

```js
var str4 = '  abc   ';
alert(1 + str4.trim() + 1);
```

输出的内容是 `1abc1` 。这就是 `trim()` 函数的作用。

`trim()` 函数在以后开发中还是比较常用的，例如下图所示是登陆界面

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815193420418.png" alt="image-20210815193420418" style="zoom:80%;"/> 

用户在输入用户名和密码时，可能会习惯的输入一些空格，这样在我们后端程序中判断用户名和密码是否正确，结果肯定是失败。所以我们一般都会对用户输入的字符串数据进行去除前后空格的操作。

### 4.3  自定义对象

在 JavaScript 中自定义对象特别简单，下面就是自定义对象的格式：

```js
var 对象名称 = {
    属性名称1:属性值1,
    属性名称2:属性值2,
    ...,
    函数名称:function (形参列表){},
	...
};
```

调用属性的格式：

```js
对象名.属性名
```

调用函数的格式：

```js
对象名.函数名()
```

接下来通过代码演示一下，让大家体验一下 JavaScript 中自定义对象

```js
var person = {
        name : "zhangsan",
        age : 23,
        eat: function (){
            alert("干饭~");
        }
    };


alert(person.name);  //zhangsan
alert(person.age); //23

person.eat();  //干饭~
```

## 5，BOM

BOM：Browser Object Model 浏览器对象模型。也就是 JavaScript 将浏览器的各个组成部分封装为对象。

我们要操作浏览器的各个组成部分就可以通过操作 BOM 中的对象来实现。比如：我现在想将浏览器地址栏的地址改为 `https://www.itheima.com` 就可以通过使用 BOM 中定义的 `Location` 对象的 `href` 属性，代码： `location.href = "https://itheima.com";` 

 BOM 中包含了如下对象：

* Window：浏览器窗口对象
* Navigator：浏览器对象
* Screen：屏幕对象
* History：历史记录对象
* Location：地址栏对象

下图是 BOM 中的各个对象和浏览器的各个组成部分的对应关系

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815194911914.png" alt="image-20210815194911914" style="zoom:70%;" />

BOM 中的 `Navigator` 对象和 `Screen` 对象基本不会使用，所以我们的课堂只对 `Window`、`History`、`Location` 对象进行讲解。

### 5.1  Window对象

window 对象是 JavaScript 对浏览器的窗口进行封装的对象。

#### 5.1.1  获取window对象

该对象不需要创建直接使用 `window`，其中 `window. ` 可以省略。比如我们之前使用的 `alert()` 函数，其实就是 `window` 对象的函数，在调用是可以写成如下两种

* 显式使用 `window` 对象调用

  ```js
  window.alert("abc");
  ```

* 隐式调用

  ```
  alert("abc")
  ```

#### 5.1.2  window对象属性

`window` 对象提供了用于获取其他 BOM 组成对象的属性

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815200625592.png" alt="image-20210815200625592" style="zoom:80%;" />

也就是说，我们想使用 `Location` 对象的话，就可以使用 `window` 对象获取；写成 `window.location`，而 `window.` 可以省略，简化写成 `location` 来获取 `Location` 对象。

#### 5.1.3  window对象函数

`window` 对象提供了很多函数供我们使用，而很多都不常用；下面给大家列举了一些比较常用的函数

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815201323329.png" alt="image-20210815201323329" style="zoom:80%;" />

> `setTimeout(function,毫秒值)` : 在一定的时间间隔后执行一个function，只执行一次
> `setInterval(function,毫秒值)` :在一定的时间间隔后执行一个function，循环执行

**confirm代码演示：**

```js
// confirm()，点击确定按钮，返回true，点击取消按钮，返回false
var flag = confirm("确认删除？");

alert(flag);
```

下图是 `confirm()` 函数的效果。当我们点击 `确定` 按钮，`flag` 变量值记录的就是 `true` ；当我们点击 `取消` 按钮，`flag` 变量值记录的就是 `false`。

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815201600493.png" alt="image-20210815201600493" style="zoom:80%;" />

而以后我们在页面删除数据时候如下图每一条数据后都有 `删除` 按钮，有可能是用户的一些误操作，所以对于删除操作需要用户进行再次确认，此时就需要用到 `confirm()` 函数。

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815202406490.png" alt="image-20210815202406490" style="zoom:70%;" />

**定时器代码演示：**

```js
setTimeout(function (){
    alert("hehe");
},3000);
```

当我们打开浏览器，3秒后才会弹框输出 `hehe`，并且只会弹出一次。

```js
setInterval(function (){
    alert("hehe");
},2000);
```

当我们打开浏览器，每隔2秒都会弹框输出 `hehe`。

#### 5.1.4  案例

**需求：每隔1秒，灯泡切换一次状态**

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815203345262.png" alt="image-20210815203345262" style="zoom:70%;" />

需求说明：

有如下页面效果，实现定时进行开灯、关灯功能

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815203623739.png" alt="image-20210815203623739" style="zoom:80%;" />

初始页面环境

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JavaScript演示</title>
</head>
<body>

<input type="button" onclick="on()" value="开灯">
<img id="myImage" border="0" src="../imgs/off.gif" style="text-align:center;">
<input type="button" onclick="off()" value="关灯">

<script>
    function on(){
        document.getElementById('myImage').src='../imgs/on.gif';
    }

    function off(){
        document.getElementById('myImage').src='../imgs/off.gif'
    }

</script>
</body>
</html>
```

代码实现：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JavaScript演示</title>
</head>
<body>

<input type="button" onclick="on()" value="开灯">
<img id="myImage" border="0" src="../imgs/off.gif" style="text-align:center;">
<input type="button" onclick="off()" value="关灯">

<script>
    function on(){
        document.getElementById('myImage').src='../imgs/on.gif';
    }

    function off(){
        document.getElementById('myImage').src='../imgs/off.gif'
    }
    
    //定义一个变量，用来记录灯的状态，偶数是开灯状态，奇数是关灯状态
    var x = 0;
    //使用循环定时器
    setInterval(function (){
        if(x % 2 == 0){//表示是偶数，开灯状态，调用 on() 函数
            on();
        }else {  //表示是奇数，关灯状态，调用 off() 函数
            off();
        }
        x ++;//改变变量的值
    },1000);

</script>
</body>
</html>
```

### 5.2  History对象

History 对象是 JavaScript 对历史记录进行封装的对象。

* History 对象的获取

  使用 window.history获取，其中window. 可以省略

* History 对象的函数

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815224826535.png" alt="image-20210815224826535" style="zoom:70%;" />

  这两个函数我们平时在访问其他的一些网站时经常使用对应的效果，如下图

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815225059114.png" alt="image-20210815225059114" style="zoom:80%;" />

  当我们点击向左的箭头，就跳转到前一个访问的页面，这就是 `back()` 函数的作用；当我们点击向右的箭头，就跳转到下一个访问的页面，这就是 `forward()` 函数的作用。

### 5.3  Location对象

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815225243560.png" alt="image-20210815225243560" style="zoom:80%;" />

Location 对象是 JavaScript 对地址栏封装的对象。可以通过操作该对象，跳转到任意页面。

#### 5.3.1  获取Location对象

使用 window.location获取，其中window. 可以省略

```js
window.location.方法();
location.方法();
```



#### 5.3.2  Location对象属性

Location对象提供了很对属性。以后常用的只有一个属性 `href`

<img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815225707580.png" alt="image-20210815225707580" style="zoom:80%;" />

**代码演示：**

```js
alert("要跳转了");
location.href = "https://www.baidu.com";
```

在浏览器首先会弹框显示 `要跳转了`，当我们点击了 `确定` 就会跳转到 百度 的首页。



#### 5.3.3  案例

**需求：3秒跳转到百度首页**

**分析：**

1. 3秒跳转，由此可以确定需要使用到定时器，而只跳转一次，所以使用 `setTimeOut()`
2. 要进行页面跳转，所以需要用到 `location` 对象的 `href` 属性实现

**代码实现：**

```js
document.write("3秒跳转到首页..."); 
setTimeout(function (){
    location.href = "https://www.baidu.com"
},3000);
```

## 6，DOM

### 6.1  概述

DOM：Document Object Model 文档对象模型。也就是 JavaScript 将 HTML 文档的各个组成部分封装为对象。

DOM 其实我们并不陌生，之前在学习 XML 就接触过，只不过 XML 文档中的标签需要我们写代码解析，而 HTML 文档是浏览器解析。封装的对象分为

* Document：整个文档对象
* Element：元素对象
* Attribute：属性对象
* Text：文本对象
* Comment：注释对象

如下图，左边是 HTML 文档内容，右边是 DOM 树

![image-20210815231028430](/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/image-20210815231028430.png)

**作用：**

JavaScript 通过 DOM， 就能够对 HTML进行操作了

* 改变 HTML 元素的内容
* 改变 HTML 元素的样式（CSS）
* 对 HTML DOM 事件作出反应
* 添加和删除 HTML 元素

**DOM相关概念：**

DOM 是 W3C（万维网联盟）定义了访问 HTML 和 XML 文档的标准。该标准被分为 3 个不同的部分：

1. 核心 DOM：针对任何结构化文档的标准模型。 XML 和 HTML 通用的标准

   * Document：整个文档对象

   * Element：元素对象

   * Attribute：属性对象

   * Text：文本对象

   * Comment：注释对象

2. XML DOM： 针对 XML 文档的标准模型

3. HTML DOM： 针对 HTML 文档的标准模型

   该标准是在核心 DOM 基础上，对 HTML 中的每个标签都封装成了不同的对象

   * 例如：`<img>` 标签在浏览器加载到内存中时会被封装成 `Image` 对象，同时该对象也是 `Element` 对象。
   * 例如：`<input type='button'>` 标签在浏览器加载到内存中时会被封装成 `Button` 对象，同时该对象也是 `Element` 对象。

### 6.2  获取 Element对象

HTML 中的 Element 对象可以通过 `Document` 对象获取，而 `Document` 对象是通过 `window` 对象获取。

`Document` 对象中提供了以下获取 `Element` 元素对象的函数

* `getElementById()`：根据id属性值获取，返回单个Element对象
* `getElementsByTagName()`：根据标签名称获取，返回Element对象数组
* `getElementsByName()`：根据name属性值获取，返回Element对象数组
* `getElementsByClassName()`：根据class属性值获取，返回Element对象数组

**代码演示：**

下面有提前准备好的页面：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <img id="light" src="../imgs/off.gif"> <br>

    <div class="cls">传智教育</div>   <br>
    <div class="cls">黑马程序员</div> <br>

    <input type="checkbox" name="hobby"> 电影
    <input type="checkbox" name="hobby"> 旅游
    <input type="checkbox" name="hobby"> 游戏
    <br>
    <script>
		//在此处书写js代码
    </script>
</body>
</html>
```

1. 根据 `id` 属性值获取上面的 `img` 元素对象，返回单个对象

   ```js
   var img = document.getElementById("light");
   alert(img);
   ```

   结果如下：

   <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210815233232924.png" alt="image-20210815233232924" style="zoom:80%;" />

   从弹框输出的内容，也可以看出是一个图片元素对象。

2. 根据标签名称获取所有的 `div` 元素对象

   ```js
   var divs = document.getElementsByTagName("div");// 返回一个数组，数组中存储的是 div 元素对象
   // alert(divs.length);  //输出 数组的长度
   //遍历数组
   for (let i = 0; i < divs.length; i++) {
       alert(divs[i]);
   }
   ```

3. 获取所有的满足 `name = 'hobby'` 条件的元素对象

   ```js
   //3. getElementsByName：根据name属性值获取，返回Element对象数组
   var hobbys = document.getElementsByName("hobby");
   for (let i = 0; i < hobbys.length; i++) {
       alert(hobbys[i]);
   }
   ```

4. 获取所有的满足 `class='cls'` 条件的元素对象

   ```js
   //4. getElementsByClassName：根据class属性值获取，返回Element对象数组
   var clss = document.getElementsByClassName("cls");
   for (let i = 0; i < clss.length; i++) {
       alert(clss[i]);
   }
   ```

### 6.3  HTML Element对象使用

HTML 中的 `Element` 元素对象有很多，不可能全部记住，以后是根据具体的需求查阅文档使用。

下面我们通过具体的案例给大家演示文档的查询和对象的使用；下面提前给大家准备好的页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <img id="light" src="../imgs/off.gif"> <br>

    <div class="cls">传智教育</div>   <br>
    <div class="cls">黑马程序员</div> <br>

    <input type="checkbox" name="hobby"> 电影
    <input type="checkbox" name="hobby"> 旅游
    <input type="checkbox" name="hobby"> 游戏
    <br>
    <script>
        //在此处写js低吗
    </script>
</body>
</html>
```

**需求：**

1. 点亮灯泡

   此案例由于需要改变 `img` 标签 的图片，所以我们查询文档，下图是查看文档的流程：

   <img src="/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/js/assets/查看文档.png" alt="image-20210815233232924" style="zoom:100%;" />

   代码实现：

   ```js
   //1，根据 id='light' 获取 img 元素对象
   var img = document.getElementById("light");
   //2，修改 img 对象的 src 属性来改变图片
   img.src = "../imgs/on.gif";
   ```

2. 将所有的 `div` 标签的标签体内容替换为 `呵呵`

   ```js
   //1，获取所有的 div 元素对象
   var divs = document.getElementsByTagName("div");
   /*
           style:设置元素css样式
           innerHTML：设置元素内容
       */
   //2，遍历数组，获取到每一个 div 元素对象，并修改元素内容
   for (let i = 0; i < divs.length; i++) {
       //divs[i].style.color = 'red';
       divs[i].innerHTML = "呵呵";
   }
   ```

3. 使所有的复选框呈现被选中的状态

   此案例我们需要看 复选框 元素对象有什么属性或者函数是来操作 复选框的选中状态。下图是文档的查看

   ![image-20210816000520457](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816000520457.png)

   代码实现：

   ```js
   //1，获取所有的 复选框 元素对象
   var hobbys = document.getElementsByName("hobby");
   //2，遍历数组，通过将 复选框 元素对象的 checked 属性值设置为 true 来改变复选框的选中状态
   for (let i = 0; i < hobbys.length; i++) {
       hobbys[i].checked = true;
   }
   ```

## 7，事件监听

要想知道什么是事件监听，首先先聊聊什么是事件？

HTML 事件是发生在 HTML 元素上的“事情”。比如：页面上的 `按钮被点击`、`鼠标移动到元素之上`、`按下键盘按键` 等都是事件。

事件监听是JavaScript 可以在事件被侦测到时==执行一段逻辑代码。==例如下图当我们点击 `开灯` 按钮，就需要通过 js 代码实现替换图片

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816194143246.png" alt="image-20210816194143246" style="zoom:80%;" />

再比如下图输入框，当我们输入了用户名 `光标离开` 输入框，就需要通过 js 代码对输入的内容进行校验，没通过校验就在输入框后提示 `用户名格式有误!`

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816194333252.png" alt="image-20210816194333252" style="zoom:90%;" />

### 7.1  事件绑定

JavaScript 提供了两种事件绑定方式：

* 方式一：通过 HTML标签中的事件属性进行绑定

  如下面代码，有一个按钮元素，我们是在该标签上定义 `事件属性`，在事件属性中绑定函数。`onclick` 就是 `单击事件` 的事件属性。`onclick='on（）'` 表示该点击事件绑定了一个名为 `on()` 的函数

  ```html
  <input type="button" onclick='on()’>
  ```

  下面是点击事件绑定的 `on()` 函数

  ```js
  function on(){
  	alert("我被点了");
  }
  ```

* 方式二：通过 DOM 元素属性绑定

  如下面代码是按钮标签，在该标签上我们并没有使用 `事件属性`，绑定事件的操作需要在 js 代码中实现

  ```html
  <input type="button" id="btn">
  ```

  下面 js 代码是获取了 `id='btn'` 的元素对象，然后将 `onclick` 作为该对象的属性，并且绑定匿名函数。该函数是在事件触发后自动执行

  ```js
  document.getElementById("btn").onclick = function (){
      alert("我被点了");
  }
  ```

**代码演示：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!--方式1：在下面input标签上添加 onclick 属性，并绑定 on() 函数-->
    <input type="button" value="点我" onclick="on()"> <br>
    <input type="button" value="再点我" id="btn">

    <script>
        function on(){
            alert("我被点了");
        }
      	//方式2：获取 id="btn" 元素对象，通过调用 onclick 属性 绑定点击事件
        document.getElementById("btn").onclick = function (){
            alert("我被点了");
        }
    </script>
</body>
</html>
```

### 7.2  常见事件

上面案例中使用到了 `onclick` 事件属性，那都有哪些事件属性供我们使用呢？下面就给大家列举一些比较常用的事件属性

| 事件属性名  | 说明                     |
| ----------- | ------------------------ |
| onclick     | 鼠标单击事件             |
| onblur      | 元素失去焦点             |
| onfocus     | 元素获得焦点             |
| onload      | 某个页面或图像被完成加载 |
| onsubmit    | 当表单提交时触发该事件   |
| onmouseover | 鼠标被移到某元素之上     |
| onmouseout  | 鼠标从某元素移开         |

* `onfocus` 获得焦点事件。

  如下图，当点击了输入框后，输入框就获得了焦点。而下图示例是当获取焦点后会更改输入框的背景颜色。

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816214900928.png" alt="image-20210816214900928" style="zoom:80%;" />

* `onblur  ` 失去焦点事件。

  如下图，当点击了输入框后，输入框就获得了焦点；再点击页面其他位置，那输入框就失去焦点了。下图示例是将输入的文本转换为大写。

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816215235969.png" alt="image-20210816215235969" style="zoom:80%;" />

* `onmouseout  ` 鼠标移出事件。

* `onmouseover  `  鼠标移入事件。

  如下图，当鼠标移入到 苹果 图片上时，苹果图片变大；当鼠标移出 苹果图片时，苹果图片变小。

  <img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816220149093.png" alt="image-20210816220149093" style="zoom:70%;" />

* `onsubmit  ` 表单提交事件

  如下是带有表单的页面

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
      <form id="register" action="#" >
          <input type="text" name="username" />
          <input type="submit" value="提交">
      </form>
      <script>
          
      </script>
  </body>
  </html>
  ```

  如上代码的表单，当我们点击 `提交` 按钮后，表单就会提交，此处默认使用的是 `GET` 提交方式，会将提交的数据拼接到 URL 后。现需要通过 js 代码实现阻止表单提交的功能，js 代码实现如下：

  1. 获取 `form` 表单元素对象。
  2. 给 `form` 表单元素对象绑定 `onsubmit` 事件，并绑定匿名函数。
  3. 该匿名函数如果返回的是true，提交表单；如果返回的是false，阻止表单提交。

  ```js
  document.getElementById("register").onsubmit = function (){
      //onsubmit 返回true，则表单会被提交，返回false，则表单不提交
      return true;
  }
  ```

## 8，表单验证案例

### 8.1  需求

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816225925955.png" alt="image-20210816225925955" style="zoom:60%;" />

有如下注册页面，对表单进行校验，如果输入的用户名、密码、手机号符合规则，则允许提交；如果不符合规则，则不允许提交。

完成以下需求：

1. 当输入框失去焦点时，验证输入内容是否符合要求

2. 当点击注册按钮时，判断所有输入框的内容是否都符合要求，如果不合符则阻止表单提交

### 8.2  环境准备

下面是初始页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>欢迎注册</title>
    <link href="../css/register.css" rel="stylesheet">
</head>
<body>
    <div class="form-div">
        <div class="reg-content">
            <h1>欢迎注册</h1>
            <span>已有帐号？</span> <a href="#">登录</a>
        </div>
        <form id="reg-form" action="#" method="get">
            <table>
                <tr>
                    <td>用户名</td>
                    <td class="inputs">
                        <input name="username" type="text" id="username">
                        <br>
                        <span id="username_err" class="err_msg" style="display: none">用户名不太受欢迎</span>
                    </td>
                </tr>

                <tr>
                    <td>密码</td>
                    <td class="inputs">
                        <input name="password" type="password" id="password">
                        <br>
                        <span id="password_err" class="err_msg" style="display: none">密码格式有误</span>
                    </td>
                </tr>

                <tr>
                    <td>手机号</td>
                    <td class="inputs"><input name="tel" type="text" id="tel">
                        <br>
                        <span id="tel_err" class="err_msg" style="display: none">手机号格式有误</span>
                    </td>
                </tr>
            </table>
            <div class="buttons">
                <input value="注 册" type="submit" id="reg_btn">
            </div>
            <br class="clear">
        </form>

    </div>


    <script>

    </script>
</body>
</html>
```

### 8.3  验证输入框

此小节完成如下功能：

* 校验用户名。当用户名输入框失去焦点时，判断输入的内容是否符合 `长度是 6-12 位` 规则，不符合使 `id='username_err'` 的span标签显示出来，给出用户提示。
* 校验密码。当密码输入框失去焦点时，判断输入的内容是否符合 `长度是 6-12 位` 规则，不符合使 `id='password_err'` 的span标签显示出来，给出用户提示。
* 校验手机号。当手机号输入框失去焦点时，判断输入的内容是否符合 `长度是 11 位` 规则，不符合使 `id='tel_err'` 的span标签显示出来，给出用户提示。

代码如下：

```js
//1. 验证用户名是否符合规则
//1.1 获取用户名的输入框
var usernameInput = document.getElementById("username");

//1.2 绑定onblur事件 失去焦点
usernameInput.onblur = function () {
    //1.3 获取用户输入的用户名
    var username = usernameInput.value.trim();

    //1.4 判断用户名是否符合规则：长度 6~12
    if (username.length >= 6 && username.length <= 12) {
        //符合规则
        document.getElementById("username_err").style.display = 'none';
    } else {
        //不合符规则
        document.getElementById("username_err").style.display = '';
    }
}

//1. 验证密码是否符合规则
//1.1 获取密码的输入框
var passwordInput = document.getElementById("password");

//1.2 绑定onblur事件 失去焦点
passwordInput.onblur = function() {
    //1.3 获取用户输入的密码
    var password = passwordInput.value.trim();

    //1.4 判断密码是否符合规则：长度 6~12
    if (password.length >= 6 && password.length <= 12) {
        //符合规则
        document.getElementById("password_err").style.display = 'none';
    } else {
        //不合符规则
        document.getElementById("password_err").style.display = '';
    }
}

//1. 验证手机号是否符合规则
//1.1 获取手机号的输入框
var telInput = document.getElementById("tel");

//1.2 绑定onblur事件 失去焦点
telInput.onblur = function() {
    //1.3 获取用户输入的手机号
    var tel = telInput.value.trim();

    //1.4 判断手机号是否符合规则：长度 11
    if (tel.length == 11) {
        //符合规则
        document.getElementById("tel_err").style.display = 'none';
    } else {
        //不合符规则
        document.getElementById("tel_err").style.display = '';
    }
}
```

### 8.3  验证表单

当用户点击 `注册` 按钮时，需要同时对输入的 `用户名`、`密码`、`手机号` ，如果都符合规则，则提交表单；如果有一个不符合规则，则不允许提交表单。实现该功能需要获取表单元素对象，并绑定 `onsubmit` 事件

```js
//1. 获取表单对象
var regForm = document.getElementById("reg-form");

//2. 绑定onsubmit 事件
regForm.onsubmit = function () {
    
}
```

`onsubmit` 事件绑定的函数需要对输入的 `用户名`、`密码`、`手机号` 进行校验，这些校验我们之前都已经实现过了，这里我们还需要再校验一次吗？不需要，只需要对之前校验的代码进行改造，把每个校验的代码专门抽象到有名字的函数中，方便调用；并且每个函数都要返回结果来去决定是提交表单还是阻止表单提交，代码如下：

```js
//1. 验证用户名是否符合规则
//1.1 获取用户名的输入框
var usernameInput = document.getElementById("username");

//1.2 绑定onblur事件 失去焦点
usernameInput.onblur = checkUsername;

function checkUsername() {
    //1.3 获取用户输入的用户名
    var username = usernameInput.value.trim();

    //1.4 判断用户名是否符合规则：长度 6~12
    var flag = username.length >= 6 && username.length <= 12;
    if (flag) {
        //符合规则
        document.getElementById("username_err").style.display = 'none';
    } else {
        //不合符规则
        document.getElementById("username_err").style.display = '';
    }
    return flag;
}

//1. 验证密码是否符合规则
//1.1 获取密码的输入框
var passwordInput = document.getElementById("password");

//1.2 绑定onblur事件 失去焦点
passwordInput.onblur = checkPassword;

function checkPassword() {
    //1.3 获取用户输入的密码
    var password = passwordInput.value.trim();

    //1.4 判断密码是否符合规则：长度 6~12
    var flag = password.length >= 6 && password.length <= 12;
    if (flag) {
        //符合规则
        document.getElementById("password_err").style.display = 'none';
    } else {
        //不合符规则
        document.getElementById("password_err").style.display = '';
    }
    return flag;
}

//1. 验证手机号是否符合规则
//1.1 获取手机号的输入框
var telInput = document.getElementById("tel");

//1.2 绑定onblur事件 失去焦点
telInput.onblur = checkTel;

function checkTel() {
    //1.3 获取用户输入的手机号
    var tel = telInput.value.trim();

    //1.4 判断手机号是否符合规则：长度 11
    var flag = tel.length == 11;
    if (flag) {
        //符合规则
        document.getElementById("tel_err").style.display = 'none';
    } else {
        //不合符规则
        document.getElementById("tel_err").style.display = '';
    }
    return flag;
}
```

而 `onsubmit` 绑定的函数需要调用 `checkUsername()` 函数、`checkPassword()` 函数、`checkTel()` 函数。

```js
//1. 获取表单对象
var regForm = document.getElementById("reg-form");

//2. 绑定onsubmit 事件
regForm.onsubmit = function () {
    //挨个判断每一个表单项是否都符合要求，如果有一个不合符，则返回false

    var flag = checkUsername() && checkPassword() && checkTel();

    return flag;
}
```

## 9，RegExp对象

RegExp 是正则对象。正则对象是判断指定字符串是否符合规则。

如下图是百度贴吧中的帖子

<img src="https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20210816235112754.png" alt="image-20210816235112754" style="zoom:70%;" />

我们可以通过爬虫技术去爬取该页面源代码，然后获取页面中所有的邮箱，后期我们可以给这些邮箱地址发送推广的邮件。那么问题来了，如何才能知道页面内容中哪些事邮箱地址呢？这里就可以使用正则表达式来匹配邮箱。

在 js 中对正则表达式封装的对象就是正则对象。

### 9.1  正则对象使用

#### 9.1.1  创建对象

正则对象有两种创建方式：

* 直接量方式：注意不要加引号

  ```js
  var reg = /正则表达式/;
  ```

* 创建 RegExp 对象

  ```js
  var reg = new RegExp("正则表达式");
  ```

#### 9.1.2  函数

`test(str)` ：判断指定字符串是否符合规则，返回 true或 false

### 9.2  正则表达式

从上面创建正则对象的格式中可以看出不管哪种方式都需要正则表达式，那么什么是正则表达式呢？

正则表达式定义了字符串组成的规则。也就是判断指定的字符串是否符合指定的规则，如果符合返回true，如果不符合返回false。

正则表达式是和语言无关的。很多语言都支持正则表达式，Java语言也支持，只不过正则表达式在不同的语言中的使用方式不同，js 中需要使用正则对象来使用正则表达式。

正则表达式常用的规则如下：

* ^：表示开始

* $：表示结束

* [ ]：代表某个范围内的单个字符，比如： [0-9] 单个数字字符

* .：代表任意单个字符，除了换行和行结束符

* \w：代表单词字符：字母、数字、下划线(_)，相当于 [A-Za-z0-9_]

* \d：代表数字字符： 相当于 [0-9]

量词：

* +：至少一个

* *：零个或多个

* ？：零个或一个

* {x}：x个

* {m,}：至少m个

* {m,n}：至少m个，最多n个

**代码演示：**

```js
// 规则：单词字符，6~12
//1,创建正则对象，对正则表达式进行封装
var reg = /^\w{6,12}$/;

var str = "abcccc";
//2,判断 str 字符串是否符合 reg 封装的正则表达式的规则
var flag = reg.test(str);
alert(flag);
```

### 9.3  改进表单校验案例

表单校验案例中的规则是我们进行一系列的判断来实现的，现在学习了正则对象后，就可以使用正则对象来改进这个案例。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>欢迎注册</title>
    <link href="../css/register.css" rel="stylesheet">
</head>
<body>

<div class="form-div">
    <div class="reg-content">
        <h1>欢迎注册</h1>
        <span>已有帐号？</span> <a href="#">登录</a>
    </div>
    <form id="reg-form" action="#" method="get">

        <table>

            <tr>
                <td>用户名</td>
                <td class="inputs">
                    <input name="username" type="text" id="username">
                    <br>
                    <span id="username_err" class="err_msg" style="display: none">用户名不太受欢迎</span>
                </td>

            </tr>

            <tr>
                <td>密码</td>
                <td class="inputs">
                    <input name="password" type="password" id="password">
                    <br>
                    <span id="password_err" class="err_msg" style="display: none">密码格式有误</span>
                </td>
            </tr>


            <tr>
                <td>手机号</td>
                <td class="inputs"><input name="tel" type="text" id="tel">
                    <br>
                    <span id="tel_err" class="err_msg" style="display: none">手机号格式有误</span>
                </td>
            </tr>

        </table>

        <div class="buttons">
            <input value="注 册" type="submit" id="reg_btn">
        </div>
        <br class="clear">
    </form>

</div>


<script>

    //1. 验证用户名是否符合规则
    //1.1 获取用户名的输入框
    var usernameInput = document.getElementById("username");

    //1.2 绑定onblur事件 失去焦点
    usernameInput.onblur = checkUsername;

    function checkUsername() {
        //1.3 获取用户输入的用户名
        var username = usernameInput.value.trim();

        //1.4 判断用户名是否符合规则：长度 6~12,单词字符组成
        var reg = /^\w{6,12}$/;
        var flag = reg.test(username);

        //var flag = username.length >= 6 && username.length <= 12;
        if (flag) {
            //符合规则
            document.getElementById("username_err").style.display = 'none';
        } else {
            //不合符规则
            document.getElementById("username_err").style.display = '';
        }
        return flag;
    }

    //1. 验证密码是否符合规则
    //1.1 获取密码的输入框
    var passwordInput = document.getElementById("password");

    //1.2 绑定onblur事件 失去焦点
    passwordInput.onblur = checkPassword;

    function checkPassword() {
        //1.3 获取用户输入的密码
        var password = passwordInput.value.trim();

        //1.4 判断密码是否符合规则：长度 6~12
        var reg = /^\w{6,12}$/;
        var flag = reg.test(password);

        //var flag = password.length >= 6 && password.length <= 12;
        if (flag) {
            //符合规则
            document.getElementById("password_err").style.display = 'none';
        } else {
            //不合符规则
            document.getElementById("password_err").style.display = '';
        }
        return flag;
    }

    //1. 验证手机号是否符合规则
    //1.1 获取手机号的输入框
    var telInput = document.getElementById("tel");

    //1.2 绑定onblur事件 失去焦点
    telInput.onblur = checkTel;

    function checkTel() {
        //1.3 获取用户输入的手机号
        var tel = telInput.value.trim();

        //1.4 判断手机号是否符合规则：长度 11，数字组成，第一位是1
        //var flag = tel.length == 11;
        var reg = /^[1]\d{10}$/;
        var flag = reg.test(tel);
        if (flag) {
            //符合规则
            document.getElementById("tel_err").style.display = 'none';
        } else {
            //不合符规则
            document.getElementById("tel_err").style.display = '';
        
        return flag;
    }

    //1. 获取表单对象
    var regForm = document.getElementById("reg-form");

    //2. 绑定onsubmit 事件
    regForm.onsubmit = function () {
        //挨个判断每一个表单项是否都符合要求，如果有一个不合符，则返回false

        var flag = checkUsername() && checkPassword() && checkTel();

        return flag;
    }
</script>
</body>
</html>
```

## 	HTTP&Tomcat&Servlet

**今日目标：**

> * 了解JavaWeb开发的技术栈
> * 理解HTTP协议和HTTP请求与响应数据的格式
> * 掌握Tomcat的使用
> * 掌握在IDEA中使用Tomcat插件
> * 理解Servlet的执行流程和生命周期
> * 掌握Servlet的使用和相关配置

## 1，Web概述

### 1.1 Web和JavaWeb的概念

==Web是全球广域网，也称为万维网(www)，能够通过浏览器访问的网站。==
在我们日常的生活中，经常会使用浏览器去访问`百度`、`京东`、`传智官网`等这些网站，这些网站统称为Web网站。如下就是通过浏览器访问传智官网的界面: 
![ ](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627031023395.png)
我们知道了什么是Web，那么JavaWeb又是什么呢？顾名思义==JavaWeb就是用Java技术来解决相关web互联网领域的技术栈。==
等学习完JavaWeb之后，同学们就可以使用Java语言开发我们上述所说的网站。而国内很多大型网站公司也是首选Java语言来解决web互联网相关的问题。
使用Java语言开发互联网系统是有很多技术栈需要大家了解，具体都有哪些呢?

### 1.2 JavaWeb技术栈

了解JavaWeb技术栈之前，有一个很重要的概念要介绍。

#### 1.2.1 B/S架构

什么是B/S架构?
B/S 架构：Browser/Server，浏览器/服务器 架构模式，它的特点是，客户端只需要浏览器，应用程序的逻辑和数据都存储在服务器端。浏览器只需要请求服务器，获取Web资源，服务器把Web资源发送给浏览器即可。大家可以通过下面这张图来回想下我们平常的上网过程:
![1627031933553](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627031933553.png)

* 打开浏览器访问百度首页，输入要搜索的内容，点击回车或百度一下，就可以获取和搜索相关的内容
* 思考下搜索的内容并不在我们自己的点上，那么这些内容从何而来？答案很明显是从百度服务器返回给我们的
* 日常百度的小细节，逢年过节百度的logo会更换不同的图片，服务端发生变化，客户端不需做任务事情就能获取最新内容
* 所以说B/S架构的好处:易于维护升级：服务器端升级后，客户端无需任何部署就可以使用到新的版本。
  了解了什么是B/S架构后，作为后台开发工程师的我们将来主要关注的是服务端的开发和维护工作。在服务端将来会放很多资源,都有哪些资源呢?

#### 1.2.2 静态资源

* 静态资源主要包含HTML、CSS、JavaScript、图片等，主要负责页面的展示。
* 我们之前已经学过前端网页制作`三剑客`(HTML+CSS+JavaScript),使用这些技术我们就可以制作出效果比较丰富的网页，将来展现给用户。但是由于做出来的这些内容都是静态的，这就会导致所有的人看到的内容将是一模一样。
* 在日常上网的过程中，我们除了看到这些好看的页面以外，还会碰到很多动态内容，比如我们常见的百度登录效果:
  ![1627037814180](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627037814180.png)
  `张三`登录以后在网页的右上角看到的是 `张三`，而`李四`登录以后看到的则是`李四`。所以不同的用户访问相同的资源看到的内容大多数是不一样的，要想实现这样的效果，光靠静态资源是无法实现的。

#### 1.2.3 动态资源

* 动态资源主要包含Servlet、JSP等，主要用来负责逻辑处理。
* 动态资源处理完逻辑后会把得到的结果交给静态资源来进行展示，动态资源和静态资源要结合一起使用。
* 动态资源虽然可以处理逻辑，但是当用户来登录百度的时候，就需要输入`用户名`和`密码`,这个时候我们就又需要解决的一个问题是，用户在注册的时候填入的用户名和密码、以及我们经常会访问到一些数据列表的内容展示(如下图所示)，这些数据都存储在哪里?我们需要的时候又是从哪里来取呢?
  ![1627038674340](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627038674340.png)

#### 1.2.4 数据库

* 数据库主要负责存储数据。
* 整个Web的访问过程就如下图所示:
  ![1627039320220](/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/http/assets/1627039320220.png)
  (1)浏览器发送一个请求到服务端，去请求所需要的相关资源;
  (2)资源分为动态资源和静态资源,动态资源可以是使用Java代码按照Servlet和JSP的规范编写的内容;
  (3)在Java代码可以进行业务处理也可以从数据库中读取数据;
  (4)拿到数据后，把数据交给HTML页面进行展示,再结合CSS和JavaScript使展示效果更好;
  (5)服务端将静态资源响应给浏览器;
  (6)浏览器将这些资源进行解析;
  (7)解析后将效果展示在浏览器，用户就可以看到最终的结果。
  在整个Web的访问过程中，会设计到很多技术，这些技术有已经学习过的，也有还未涉及到的内容，都有哪些还没有涉及到呢?

#### 1.2.5 HTTP协议

* HTTP协议:主要定义通信规则
* 浏览器发送请求给服务器，服务器响应数据给浏览器，这整个过程都需要遵守一定的规则，之前大家学习过TCP、UDP，这些都属于规则，这里我们需要使用的是HTTP协议，这也是一种规则。

#### 1.2.6 Web服务器

* Web服务器:负责解析 HTTP 协议，解析请求数据，并发送响应数据
* 浏览器按照HTTP协议发送请求和数据，后台就需要一个Web服务器软件来根据HTTP协议解析请求和数据，然后把处理结果再按照HTTP协议发送给浏览器
* Web服务器软件有很多，我们课程中将学习的是目前最为常用的==Tomcat==服务器

到这为止，关于JavaWeb中用到的技术栈我们就介绍完了，这里面就只有HTTP协议、Servlet、JSP以及Tomcat这些知识是没有学习过的，所以整个Web核心主要就是来学习这些技术。

### 1.3 Web核心课程安排

![1627043194238](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627043194238.png)

整个Web核心，我们总共有六天的学习内容，分别是:

* 第一天：HTTP、Tomcat、Servlet
* 第二天：Request(请求)、Response(响应)
* 第三天：JSP、会话技术(Cookie、Session)
* 第四天：Filter(过滤器)、Listener(监听器)
* 第五天：Ajax、Vue、ElementUI
* 第六天：综合案例

(1)Request是从客户端向服务端发出的请求对象，

(2)Response是从服务端响应给客户端的结果对象，

(3)JSP是动态网页技术,

(4)会话技术是用来存储客户端和服务端交互所产生的数据，

(5)过滤器是用来拦截客户端的请求,

(6)监听器是用来监听特定事件,

(7)Ajax、Vue、ElementUI都是属于前端技术

这些技术都该如何来使用，我们后面会一个个进行详细的讲解。接下来我们来学习下HTTP、Tomcat和Servlet。 

## 2, HTTP

### 2.1 简介

**HTTP概念**

HyperText Transfer Protocol，超文本传输协议，规定了浏览器和服务器之间==数据传输的规则==。

* 数据传输的规则指的是请求数据和响应数据需要按照指定的格式进行传输。
* 如果想知道具体的格式，可以打开浏览器，点击`F12`打开开发者工具，点击`Network`来查看某一次请求的请求数据和响应数据具体的格式内容，如下图所示:

![1627046235092](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627046235092.png)

> 注意:在浏览器中如果看不到上述内容，需要清除浏览器的浏览数据。chrome浏览器可以使用ctrl+shift+Del进行清除。

==所以学习HTTP主要就是学习请求和响应数据的具体格式内容。==

**HTTP协议特点**

HTTP协议有它自己的一些特点，分别是:

* 基于TCP协议: 面向连接，安全

  TCP是一种面向连接的(建立连接之前是需要经过三次握手)、可靠的、基于字节流的传输层通信协议，在数据传输方面更安全。

* 基于请求-响应模型的:一次请求对应一次响应

  请求和响应是一一对应关系

* HTTP协议是无状态协议:对于事物处理没有记忆能力。每次请求-响应都是独立的

  无状态指的是客户端发送HTTP请求给服务端之后，服务端根据请求响应数据，响应完后，不会记录任何信息。这种特性有优点也有缺点，

  * 缺点:多次请求间不能共享数据
  * 优点:速度快

  请求之间无法共享数据会引发的问题，如:

  * 京东购物，`加入购物车`和`去购物车结算`是两次请求，
  * HTTP协议的无状态特性，加入购物车请求响应结束后，并未记录加入购物车是何商品
  * 发起去购物车结算的请求后，因为无法获取哪些商品加入了购物车，会导致此次请求无法正确展示数据

  具体使用的时候，我们发现京东是可以正常展示数据的，原因是Java早已考虑到这个问题，并提出了使用`会话技术(Cookie、Session)`来解决这个问题。具体如何来做，我们后面会详细讲到。刚才提到HTTP协议是规定了请求和响应数据的格式，那具体的格式是什么呢?

### 2.2 请求数据格式

#### 2.2.1 格式介绍

请求数据总共分为三部分内容，分别是==请求行==、==请求头==、==请求体==

![1627050004221](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627050004221.png)

* 请求行: HTTP请求中的第一行数据，请求行包含三块内容，分别是 GET[请求方式] /[请求URL路径] HTTP/1.1[HTTP协议及版本]

  请求方式有七种,最常用的是GET和POST

* 请求头: 第二行开始，格式为key: value形式

  请求头中会包含若干个属性，常见的HTTP请求头有:

  ```
  Host: 表示请求的主机名
  User-Agent: 浏览器版本,例如Chrome浏览器的标识类似Mozilla/5.0 ...Chrome/79，IE浏览器的标识类似Mozilla/5.0 (Windows NT ...)like Gecko；
  Accept：表示浏览器能接收的资源类型，如text/*，image/*或者*/*表示所有；
  Accept-Language：表示浏览器偏好的语言，服务器可以据此返回不同语言的网页；
  Accept-Encoding：表示浏览器可以支持的压缩类型，例如gzip, deflate等。
  ```

   ==这些数据有什么用处?==

  举例说明:服务端可以根据请求头中的内容来获取客户端的相关信息，有了这些信息服务端就可以处理不同的业务需求，比如:

  * 不同浏览器解析HTML和CSS标签的结果会有不一致，所以就会导致相同的代码在不同的浏览器会出现不同的效果
  * 服务端根据客户端请求头中的数据获取到客户端的浏览器类型，就可以根据不同的浏览器设置不同的代码来达到一致的效果
  * 这就是我们常说的浏览器兼容问题

* 请求体: POST请求的最后一部分，存储请求参数

  ![1627050930378](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627050930378.png)

  如上图红线框的内容就是请求体的内容，请求体和请求头之间是有一个空行隔开。此时浏览器发送的是POST请求，为什么不能使用GET呢?这时就需要回顾GET和POST两个请求之间的区别了:

  * GET请求请求参数在请求行中，没有请求体，POST请求请求参数在请求体中
  * GET请求请求参数大小有限制，POST没有

#### 2.2.2 实例演示

把 `代码\http` 拷贝到IDEA的工作目录中，比如`D:\workspace\web`目录，

![1627278511902](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627278511902.png)

使用IDEA打开

![1627278583127](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627278583127.png)

打开后，可以点击项目中的`html\19-表单验证.html`，使用浏览器打开，通过修改页面中form表单的method属性来测试GET请求和POST请求的参数携带方式。

![1627278725007](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627278725007.png)



**小结**:

1. 请求数据中包含三部分内容，分别是请求行、请求头和请求体

2. POST请求数据在请求体中，GET请求数据在请求行上

### 2.3 响应数据格式

#### 2.3.1 格式介绍

响应数据总共分为三部分内容，分别是==响应行==、==响应头==、==响应体==

![1627053710214](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627053710214.png)

* 响应行：响应数据的第一行,响应行包含三块内容，分别是 HTTP/1.1[HTTP协议及版本] 200[响应状态码] ok[状态码的描述]

* 响应头：第二行开始，格式为key：value形式

  响应头中会包含若干个属性，常见的HTTP响应头有:

  ```
  Content-Type：表示该响应内容的类型，例如text/html，image/jpeg；
  Content-Length：表示该响应内容的长度（字节数）；
  Content-Encoding：表示该响应压缩算法，例如gzip；
  Cache-Control：指示客户端应如何缓存，例如max-age=300表示可以最多缓存300秒
  ```

* 响应体： 最后一部分。存放响应数据

  上图中<html>...</html>这部分内容就是响应体，它和响应头之间有一个空行隔开。

#### 2.3.2 响应状态码

参考: 资料/1.HTTP/《响应状态码.md》

关于响应状态码，我们先主要认识三个状态码，其余的等后期用到了再去掌握:

* 200  ok 客户端请求成功
* 404  Not Found 请求资源不存在
* 500 Internal Server Error 服务端发生不可预期的错误

#### 2.3.3 自定义服务器

在前面我们导入到IDEA中的http项目中，有一个Server.java类，这里面就是自定义的一个服务器代码，主要使用到的是`ServerSocket`和`Socket`

```java
package com.itheima;

import sun.misc.IOUtils;

import java.io.*;
import java.net.ServerSocket;
import java.net.Socket;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
/*
    自定义服务器
 */
public class Server {
    public static void main(String[] args) throws IOException {
        ServerSocket ss = new ServerSocket(8080); // 监听指定端口
        System.out.println("server is running...");
        while (true){
            Socket sock = ss.accept();
            System.out.println("connected from " + sock.getRemoteSocketAddress());
            Thread t = new Handler(sock);
            t.start();
        }
    }
}

class Handler extends Thread {
    Socket sock;

    public Handler(Socket sock) {
        this.sock = sock;
    }

    public void run() {
        try (InputStream input = this.sock.getInputStream()) {
            try (OutputStream output = this.sock.getOutputStream()) {
                handle(input, output);
            }
        } catch (Exception e) {
            try {
                this.sock.close();
            } catch (IOException ioe) {
            }
            System.out.println("client disconnected.");
        }
    }

    private void handle(InputStream input, OutputStream output) throws IOException {
        BufferedReader reader = new BufferedReader(new InputStreamReader(input, StandardCharsets.UTF_8));
        BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(output, StandardCharsets.UTF_8));
        // 读取HTTP请求:
        boolean requestOk = false;
        String first = reader.readLine();
        if (first.startsWith("GET / HTTP/1.")) {
            requestOk = true;
        }
        for (;;) {
            String header = reader.readLine();
            if (header.isEmpty()) { // 读取到空行时, HTTP Header读取完毕
                break;
            }
            System.out.println(header);
        }
        System.out.println(requestOk ? "Response OK" : "Response Error");
        if (!requestOk) {
            // 发送错误响应:
            writer.write("HTTP/1.0 404 Not Found\r\n");
            writer.write("Content-Length: 0\r\n");
            writer.write("\r\n");
            writer.flush();
        } else {
            // 发送成功响应:

            //读取html文件，转换为字符串
            BufferedReader br = new BufferedReader(new FileReader("http/html/a.html"));
            StringBuilder data = new StringBuilder();
            String line = null;
            while ((line = br.readLine()) != null){
                data.append(line);
            }
            br.close();
            int length = data.toString().getBytes(StandardCharsets.UTF_8).length;

            writer.write("HTTP/1.1 200 OK\r\n");
            writer.write("Connection: keep-alive\r\n");
            writer.write("Content-Type: text/html\r\n");
            writer.write("Content-Length: " + length + "\r\n");
            writer.write("\r\n"); // 空行标识Header和Body的分隔
            writer.write(data.toString());
            writer.flush();
        }
    }
}
```

上面代码，大家不需要自己写，主要通过上述代码，只需要大家了解到服务器可以使用java完成编写，是可以接受页面发送的请求和响应数据给前端浏览器的，真正用到的Web服务器，我们不会自己写，都是使用目前比较流行的web服务器，比如==Tomcat==

**小结**

1. 响应数据中包含三部分内容，分别是响应行、响应头和响应体

2. 掌握200，404，500这三个响应状态码所代表含义，分布是成功、所访问资源不存在和服务的错误

## 3, Tomcat

### 3.1 简介

#### 3.1.1 什么是Web服务器

Web服务器是一个应该程序（==软件==），对HTTP协议的操作进行封装，使得程序员不必直接对协议进行操作，让Web开发更加便捷。主要功能是"提供网上信息浏览服务"。

![1627058356051](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627058356051.png)

 Web服务器是安装在服务器端的一款软件，将来我们把自己写的Web项目部署到Web Tomcat服务器软件中，当Web服务器软件启动后，部署在Web服务器软件中的页面就可以直接通过浏览器来访问了。

**Web服务器软件使用步骤**

* 准备静态资源
* 下载安装Web服务器软件
* 将静态资源部署到Web服务器上
* 启动Web服务器使用浏览器访问对应的资源

上述内容在演示的时候，使用的是Apache下的Tomcat软件，至于Tomcat软件如何使用，后面会详细的讲到。而对于Web服务器来说，实现的方案有很多，Tomcat只是其中的一种，而除了Tomcat以外，还有很多优秀的Web服务器，比如:

![1627060368806](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627060368806.png)





Tomcat就是一款软件，我们主要是以学习如何去使用为主。具体我们会从以下这些方向去学习:

1. 简介: 初步认识下Tomcat

2. 基本使用: 安装、卸载、启动、关闭、配置和项目部署，这些都是对Tomcat的基本操作

3. IDEA中如何创建Maven Web项目

4. IDEA中如何使用Tomcat,后面这两个都是我们以后开发经常会用到的方式

首选我们来认识下Tomcat。

**Tomcat**

Tomcat的相关概念:

* Tomcat是Apache软件基金会一个核心项目，是一个开源免费的轻量级Web服务器，支持Servlet/JSP少量JavaEE规范。

* 概念中提到了JavaEE规范，那什么又是JavaEE规范呢?

  JavaEE: Java Enterprise Edition,Java企业版。指Java企业级开发的技术规范总和。包含13项技术规范:JDBC、JNDI、EJB、RMI、JSP、Servlet、XML、JMS、Java IDL、JTS、JTA、JavaMail、JAF。

* 因为Tomcat支持Servlet/JSP规范，所以Tomcat也被称为Web容器、Servlet容器。Servlet需要依赖Tomcat才能运行。

* Tomcat的官网: https://tomcat.apache.org/ 从官网上可以下载对应的版本进行使用。

**Tomcat的LOGO**

![1627176045795](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627176045795.png)

**小结**

通过这一节的学习，我们需要掌握以下内容:

1. Web服务器的作用

> 封装HTTP协议操作，简化开发
>
> 可以将Web项目部署到服务器中，对外提供网上浏览服务

2. Tomcat是一个轻量级的Web服务器，支持Servlet/JSP少量JavaEE规范，也称为Web容器，Servlet容器。

### 3.2 基本使用

Tomcat总共分两部分学习，先来学习Tomcat的基本使用，包括Tomcat的==下载、安装、卸载、启动和关闭==。

#### 3.2.1 下载

直接从官网下载

![1627178001030](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627178001030.png)

大家可以自行下载，也可以直接使用资料中已经下载好的资源，

Tomcat的软件程序  资料/2. Tomcat/apache-tomcat-8.5.68-windows-x64.zip

Tomcat的源码	资料/2. Tomcat/tomcat源码/apache-tomcat-8.5.68-src.zip

#### 3.2.2 安装

Tomcat是绿色版,直接解压即可

* 在D盘的software目录下，将`apache-tomcat-8.5.68-windows-x64.zip`进行解压缩，会得到一个`apache-tomcat-8.5.68`的目录，Tomcat就已经安装成功。

  ==注意==，Tomcat在解压缩的时候，解压所在的目录可以任意，但最好解压到一个不包含中文和空格的目录，因为后期在部署项目的时候，如果路径有中文或者空格可能会导致程序部署失败。

* 打开`apache-tomcat-8.5.68`目录就能看到如下目录结构，每个目录中包含的内容需要认识下,

  ![1627178815892](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627178815892.png)

  bin:目录下有两类文件，一种是以`.bat`结尾的，是Windows系统的可执行文件，一种是以`.sh`结尾的，是Linux系统的可执行文件。

  webapps:就是以后项目部署的目录

  到此，Tomcat的安装就已经完成。

#### 3.2.3 卸载

卸载比较简单，可以直接删除目录即可

#### 3.2.4 启动

双击: bin\startup.bat

![1627179006011](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627179006011.png)

启动后，通过浏览器访问 `http://localhost:8080`能看到Apache Tomcat的内容就说明Tomcat已经启动成功。

![1627199957728](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627199957728.png)

==注意==: 启动的过程中，控制台有中文乱码，需要修改conf/logging.prooperties

![1627199827589](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627199827589.png)

#### 3.2.5 关闭

关闭有三种方式 

* 直接x掉运行窗口:强制关闭[不建议]
* bin\shutdown.bat：正常关闭
* ctrl+c： 正常关闭

#### 3.2.6 配置

**修改端口**

* Tomcat默认的端口是8080，要想修改Tomcat启动的端口号，需要修改 conf/server.xml

![1627200509883](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627200509883.png)

> 注: HTTP协议默认端口号为80，如果将Tomcat端口号改为80，则将来访问Tomcat时，将不用输入端口号。

**启动时可能出现的错误**

* Tomcat的端口号取值范围是0-65535之间任意未被占用的端口，如果设置的端口号被占用，启动的时候就会包如下的错误

  ![1627200780590](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627200780590.png)

* Tomcat启动的时候，启动窗口一闪而过: 需要检查JAVA_HOME环境变量是否正确配置

![1627201248802](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627201248802.png)

#### 3.2.7 部署

* Tomcat部署项目： 将项目放置到webapps目录下，即部署完成。

  * 将 `资料/2. Tomcat/hello` 目录拷贝到Tomcat的webapps目录下

  * 通过浏览器访问`http://localhost/hello/a.html`，能看到下面的内容就说明项目已经部署成功。

    ![1627201572748](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627201572748.png)

    但是呢随着项目的增大，项目中的资源也会越来越多，项目在拷贝的过程中也会越来越费时间，该如何解决呢?

* 一般JavaWeb项目会被打包称==war==包，然后将war包放到Webapps目录下，Tomcat会自动解压缩war文件

  * 将 `资料/2. Tomcat/haha.war`目录拷贝到Tomcat的webapps目录下

  * Tomcat检测到war包后会自动完成解压缩，在webapps目录下就会多一个haha目录

  * 通过浏览器访问`http://localhost/haha/a.html`，能看到下面的内容就说明项目已经部署成功。

    ![1627201868752](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627201868752.png)

至此，Tomcat的部署就已经完成了，至于如何获得项目对应的war包，后期我们会借助于IDEA工具来生成。

### 3.3 Maven创建Web项目

介绍完Tomcat的基本使用后，我们来学习在IDEA中如何创建Maven Web项目，学习这种方式的原因是以后Tomcat中运行的绝大多数都是Web项目，而使用Maven工具能更加简单快捷的把Web项目给创建出来，所以Maven的Web项目具体如何来构建呢?

在真正创建Maven Web项目之前，我们先要知道Web项目长什么样子，具体的结构是什么?

#### 3.3.1 Web项目结构

Web项目的结构分为:开发中的项目和开发完可以部署的Web项目,这两种项目的结构是不一样的，我们一个个来介绍下:

* Maven Web项目结构: 开发中的项目

  ![1627202865978](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627202865978.png)

* 开发完成部署的Web项目

  ![1627202903750](/Users/xiechen/Library/Mobile Documents/com~apple~CloudDocs/3.阶段三 JavaWeb/讲义/http/assets/1627202903750.png)

  * 开发项目通过执行Maven打包命令==package==,可以获取到部署的Web项目目录
  * 编译后的Java字节码文件和resources的资源文件，会被放到WEB-INF下的classes目录下
  * pom.xml中依赖坐标对应的jar包，会被放入WEB-INF下的lib目录下

#### 3.3.2 创建Maven Web项目

介绍完Maven Web的项目结构后，接下来使用Maven来创建Web项目，创建方式有两种:使用骨架和不使用骨架

**使用骨架**

> 具体的步骤包含:
>
> 1.创建Maven项目
>
> 2.选择使用Web项目骨架
>
> 3.输入Maven项目坐标创建项目
>
> 4.确认Maven相关的配置信息后，完成项目创建
>
> 5.删除pom.xml中多余内容
>
> 6.补齐Maven Web项目缺失的目录结构

1. 创建Maven项目

   ![1627227574092](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627227574092.png)

2. 选择使用Web项目骨架

   ![1627227650406](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627227650406.png)

3. 输入Maven项目坐标创建项目

   ![1627228065007](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627228065007.png)

4. 确认Maven相关的配置信息后，完成项目创建

   ![1627228413280](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627228413280.png)

5. 删除pom.xml中多余内容，只留下面的这些内容，注意打包方式 jar和war的区别

   ![1627228584625](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627228584625.png)

6. 补齐Maven Web项目缺失的目录结构，默认没有java和resources目录，需要手动完成创建补齐，最终的目录结果如下

   ![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627228673162.png)



**不使用骨架**

>具体的步骤包含:
>
>1.创建Maven项目
>
>2.选择不使用Web项目骨架
>
>3.输入Maven项目坐标创建项目
>
>4.在pom.xml设置打包方式为war
>
>5.补齐Maven Web项目缺失webapp的目录结构
>
>6.补齐Maven Web项目缺失WEB-INF/web.xml的目录结构

1. 创建Maven项目

   ![1627229111549](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229111549.png)

2. 选择不使用Web项目骨架

   ![1627229137316](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229137316.png)

3. 输入Maven项目坐标创建项目

   ![1627229371251](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229371251.png)

4. 在pom.xml设置打包方式为war,默认是不写代表打包方式为jar

   ![1627229428161](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229428161.png)

5. 补齐Maven Web项目缺失webapp的目录结构

   ![1627229584134](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229584134.png)

6. 补齐Maven Web项目缺失WEB-INF/web.xml的目录结构

   ![1627229676800](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229676800.png)

7. 补充完后，最终的项目结构如下:

   

   

   ![1627229478030](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229478030.png)

上述两种方式，创建的web项目，都不是很全，需要手动补充内容，至于最终采用哪种方式来创建Maven Web项目，都是可以的，根据各自的喜好来选择使用即可。

**小结** 

1.掌握Maven Web项目的目录结构

2.掌握使用骨架的方式创建Maven Web项目

![1627204022604](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627204022604.png)

> 3.掌握不使用骨架的方式创建Maven Web项目

![1627204076090](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627204076090.png)

### 3.4 IDEA使用Tomcat

* Maven Web项目创建成功后，通过Maven的package命令可以将项目打包成war包，将war文件拷贝到Tomcat的webapps目录下，启动Tomcat就可以将项目部署成功，然后通过浏览器进行访问即可。
* 然而我们在开发的过程中，项目中的内容会经常发生变化，如果按照上面这种方式来部署测试，是非常不方便的
* 如何在IDEA中能快速使用Tomcat呢?

在IDEA中集成使用Tomcat有两种方式，分别是==集成本地Tomcat==和==Tomcat Maven插件==

#### 3.4.1 集成本地Tomcat

目标: 将刚才本地安装好的Tomcat8集成到IDEA中，完成项目部署，具体的实现步骤

1. 打开添加本地Tomcat的面板

   ![1627229992900](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627229992900.png)

2. 指定本地Tomcat的具体路径

   ![1627230313062](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627230313062.png)

3. 修改Tomcat的名称，此步骤可以不改，只是让名字看起来更有意义，HTTP port中的端口也可以进行修改，比如把8080改成80

   ![1627230366658](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627230366658.png)

4. 将开发项目部署项目到Tomcat中

   ![1627230913259](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627230913259.png)

   扩展内容： xxx.war和 xxx.war exploded这两种部署项目模式的区别?

   * war模式是将WEB工程打成war包，把war包发布到Tomcat服务器上

   * war exploded模式是将WEB工程以当前文件夹的位置关系发布到Tomcat服务器上
   * war模式部署成功后，Tomcat的webapps目录下会有部署的项目内容
   * war exploded模式部署成功后，Tomcat的webapps目录下没有，而使用的是项目的target目录下的内容进行部署
   * 建议大家都选war模式进行部署，更符合项目部署的实际情况

5. 部署成功后，就可以启动项目，为了能更好的看到启动的效果，可以在webapp目录下添加a.html页面

   ![1627233265351](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627233265351.png)

6. 启动成功后，可以通过浏览器进行访问测试

   ![1627232743706](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627232743706.png)

7. 最终的注意事项

   ![1627232916624](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627232916624.png)

   

至此，IDEA中集成本地Tomcat进行项目部署的内容我们就介绍完了，整体步骤如下，大家需要按照流程进行部署操作练习。

![1627205657117](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627205657117.png)

 #### 3.4.2 Tomcat Maven插件

在IDEA中使用本地Tomcat进行项目部署，相对来说步骤比较繁琐，所以我们需要一种更简便的方式来替换它，那就是直接使用Maven中的Tomcat插件来部署项目，具体的实现步骤，只需要两步，分别是:

1. 在pom.xml中添加Tomcat插件

   ```xml
   <build>
       <plugins>
       	<!--Tomcat插件 -->
           <plugin>
               <groupId>org.apache.tomcat.maven</groupId>
               <artifactId>tomcat7-maven-plugin</artifactId>
               <version>2.2</version>
           </plugin>
       </plugins>
   </build>
   ```

2. 使用Maven Helper插件快速启动项目，选中项目，右键-->Run Maven --> tomcat7:run

![1627233963315](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627233963315.png)

==注意:==

* 如果选中项目并右键点击后，看不到Run Maven和Debug Maven，这个时候就需要在IDEA中下载Maven Helper插件，具体的操作方式为: File --> Settings --> Plugins --> Maven Helper ---> Install,安装完后按照提示重启IDEA，就可以看到了。

![1627234184076](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627234184076.png)

* Maven Tomcat插件目前只有Tomcat7版本，没有更高的版本可以使用
* 使用Maven Tomcat插件，要想修改Tomcat的端口和访问路径，可以直接修改pom.xml

```xml
<build>
    <plugins>
    	<!--Tomcat插件 -->
        <plugin>
            <groupId>org.apache.tomcat.maven</groupId>
            <artifactId>tomcat7-maven-plugin</artifactId>
            <version>2.2</version>
            <configuration>
            	<port>80</port><!--访问端口号 -->
                <!--项目访问路径
					未配置访问路径: http://localhost:80/tomcat-demo2/a.html
					配置/后访问路径: http://localhost:80/a.html
					如果配置成 /hello,访问路径会变成什么?
						答案: http://localhost:80/hello/a.html
				-->
                <path>/</path>
            </configuration>
        </plugin>
    </plugins>
</build>
```

**小结**

通过这一节的学习，大家要掌握在IDEA中使用Tomcat的两种方式，集成本地Tomcat和使用Maven的Tomcat插件。后者更简单，推荐大家使用，但是如果对于Tomcat的版本有比较高的要求，要在Tomcat7以上，这个时候就只能用前者了。

## 4， Servlet

### 4.1 简介

![1627234763207](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627234763207.png)

* Servlet是JavaWeb最为核心的内容，它是Java提供的一门==动态==web资源开发技术。

* 使用Servlet就可以实现，根据不同的登录用户在页面上动态显示不同内容。

* Servlet是JavaEE规范之一，其实就是一个接口，将来我们需要定义Servlet类实现Servlet接口，并由web服务器运行Servlet

  ![1627234972853](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627234972853.png)

介绍完Servlet是什么以后，接下来我们就按照`快速入门`->`执行流程`->`生命周期`->`体系结构`->`urlPattern配置`->`XML配置`的学习步骤，一步步完成对Servlet的知识学习，首选我们来通过一个入门案例来快速把Servlet用起来。

### 4.2 快速入门

==需求分析: 编写一个Servlet类，并使用IDEA中Tomcat插件进行部署，最终通过浏览器访问所编写的Servlet程序。==

具体的实现步骤为:

1. 创建Web项目`web-demo`，导入Servlet依赖坐标

```xml
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <!--
      此处为什么需要添加该标签?
      provided指的是在编译和测试过程中有效,最后生成的war包时不会加入
       因为Tomcat的lib目录中已经有servlet-api这个jar包，如果在生成war包的时候生效就会和Tomcat中的jar包冲突，导致报错
    -->
    <scope>provided</scope>
</dependency>
```

2. 创建:定义一个类，实现Servlet接口，并重写接口中所有方法，并在service方法中输入一句话

```java
package com.itheima.web;

import javax.servlet.*;
import java.io.IOException;

public class ServletDemo1 implements Servlet {

    public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
        System.out.println("servlet hello world~");
    }
    public void init(ServletConfig servletConfig) throws ServletException {

    }

    public ServletConfig getServletConfig() {
        return null;
    }

    public String getServletInfo() {
        return null;
    }

    public void destroy() {

    }
}
```

3. 配置:在类上使用@WebServlet注解，配置该Servlet的访问路径

```java
@WebServlet("/demo1")
```

4. 访问:启动Tomcat,浏览器中输入URL地址访问该Servlet

```
http://localhost:8080/web-demo/demo1
```

5. 器访问后，在控制台会打印`servlet hello world~` 说明servlet程序已经成功运行。

至此，Servlet的入门案例就已经完成，大家可以按照上面的步骤进行练习了。

### 4.3 执行流程

Servlet程序已经能正常运行，但是我们需要思考个问题: 我们并没有创建ServletDemo1类的对象，也没有调用对象中的service方法，为什么在控制台就打印了`servlet hello world~`这句话呢?

要想回答上述问题，我们就需要对Servlet的执行流程进行一个学习。

![1627236923139](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627236923139.png)

* 浏览器发出`http://localhost:8080/web-demo/demo1`请求，从请求中可以解析出三部分内容，分别是`localhost:8080`、`web-demo`、`demo1`
  * 根据`localhost:8080`可以找到要访问的Tomcat Web服务器
  * 根据`web-demo`可以找到部署在Tomcat服务器上的web-demo项目
  * 根据`demo1`可以找到要访问的是项目中的哪个Servlet类，根据@WebServlet后面的值进行匹配
* 找到ServletDemo1这个类后，Tomcat Web服务器就会为ServletDemo1这个类创建一个对象，然后调用对象中的service方法
  * ServletDemo1实现了Servlet接口，所以类中必然会重写service方法供Tomcat Web服务器进行调用
  * service方法中有ServletRequest和ServletResponse两个参数，ServletRequest封装的是请求数据，ServletResponse封装的是响应数据，后期我们可以通过这两个参数实现前后端的数据交互

**小结**

介绍完Servlet的执行流程，需要大家掌握两个问题：

1. Servlet由谁创建?Servlet方法由谁调用?

> Servlet由web服务器创建，Servlet方法由web服务器调用

2. 服务器怎么知道Servlet中一定有service方法?

> 因为我们自定义的Servlet,必须实现Servlet接口并复写其方法，而Servlet接口中有service方法

### 4.4 生命周期

介绍完Servlet的执行流程后，我们知道Servlet是由Tomcat Web服务器帮我们创建的。

接下来咱们再来思考一个问题:==Tomcat什么时候创建的Servlet对象?==

要想回答上述问题，我们就需要对Servlet的生命周期进行一个学习。

* 生命周期: 对象的生命周期指一个对象从被创建到被销毁的整个过程。

* Servlet运行在Servlet容器(web服务器)中，其生命周期由容器来管理，分为4个阶段：

  1. ==加载和实例化==：默认情况下，当Servlet第一次被访问时，由容器创建Servlet对象

  ```xml
  默认情况，Servlet会在第一次访问被容器创建，但是如果创建Servlet比较耗时的话，那么第一个访问的人等待的时间就比较长，用户的体验就比较差，那么我们能不能把Servlet的创建放到服务器启动的时候来创建，具体如何来配置?
  
  @WebServlet(urlPatterns = "/demo1",loadOnStartup = 1)
  loadOnstartup的取值有两类情况
  	（1）负整数:第一次访问时创建Servlet对象
  	（2）0或正整数:服务器启动时创建Servlet对象，数字越小优先级越高
  ```

  2. ==初始化==：在Servlet实例化之后，容器将调用Servlet的==init()==方法初始化这个对象，完成一些如加载配置文件、创建连接等初始化的工作。该方法只==调用一次==
  3. ==请求处理==：==每次==请求Servlet时，Servlet容器都会调用Servlet的==service()==方法对请求进行处理
  4. ==服务终止==：当需要释放内存或者容器关闭时，容器就会调用Servlet实例的==destroy()==方法完成资源的释放。在destroy()方法调用之后，容器会释放这个Servlet实例，该实例随后会被Java的垃圾收集器所回收

* 通过案例演示下上述的生命周期

  ```java
  package com.itheima.web;
  
  import javax.servlet.*;
  import javax.servlet.annotation.WebServlet;
  import java.io.IOException;
  /**
  * Servlet生命周期方法
  */
  @WebServlet(urlPatterns = "/demo2",loadOnStartup = 1)
  public class ServletDemo2 implements Servlet {
  
      /**
       *  初始化方法
       *  1.调用时机：默认情况下，Servlet被第一次访问时，调用
       *      * loadOnStartup: 默认为-1，修改为0或者正整数，则会在服务器启动的时候，调用
       *  2.调用次数: 1次
       * @param config
       * @throws ServletException
       */
      public void init(ServletConfig config) throws ServletException {
          System.out.println("init...");
      }
  
      /**
       * 提供服务
       * 1.调用时机:每一次Servlet被访问时，调用
       * 2.调用次数: 多次
       * @param req
       * @param res
       * @throws ServletException
       * @throws IOException
       */
      public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
          System.out.println("servlet hello world~");
      }
  
      /**
       * 销毁方法
       * 1.调用时机：内存释放或者服务器关闭的时候，Servlet对象会被销毁，调用
       * 2.调用次数: 1次
       */
      public void destroy() {
          System.out.println("destroy...");
      }
      public ServletConfig getServletConfig() {
          return null;
      }
  
      public String getServletInfo() {
          return null;
      }
  
  
  }
  ```

  ==注意:如何才能让Servlet中的destroy方法被执行？==

  ![1627239292226](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627239292226.png)

在Terminal命令行中，先使用`mvn tomcat7:run`启动，然后再使用`ctrl+c`关闭tomcat

**小结**

这节中需要掌握的内容是:

1. Servlet对象在什么时候被创建的?

> 默认是第一次访问的时候被创建，可以使用@WebServlet(urlPatterns = "/demo2",loadOnStartup = 1)的loadOnStartup 修改成在服务器启动的时候创建。

2. Servlet生命周期中涉及到的三个方法，这三个方法是什么?什么时候被调用?调用几次?

>涉及到三个方法，分别是 init()、service()、destroy()
>
>init方法在Servlet对象被创建的时候执行，只执行1次
>
>service方法在Servlet被访问的时候调用，每访问1次就调用1次
>
>destroy方法在Servlet对象被销毁的时候调用，只执行1次

### 4.5 方法介绍

Servlet中总共有5个方法，我们已经介绍过其中的三个，剩下的两个方法作用分别是什么？

我们先来回顾下前面讲的三个方法，分别是:

* 初始化方法，在Servlet被创建时执行，只执行一次

```java
void init(ServletConfig config) 
```

* 提供服务方法， 每次Servlet被访问，都会调用该方法

```java
void service(ServletRequest req, ServletResponse res)
```

* 销毁方法，当Servlet被销毁时，调用该方法。在内存释放或服务器关闭时销毁Servlet

```java
void destroy() 
```

剩下的两个方法是:

* 获取Servlet信息

```java
String getServletInfo() 
//该方法用来返回Servlet的相关信息，没有什么太大的用处，一般我们返回一个空字符串即可
public String getServletInfo() {
    return "";
}
```

* 获取ServletConfig对象

```java
ServletConfig getServletConfig()
```

ServletConfig对象，在init方法的参数中有，而Tomcat Web服务器在创建Servlet对象的时候会调用init方法，必定会传入一个ServletConfig对象，我们只需要将服务器传过来的ServletConfig进行返回即可。具体如何操作?

```java
package com.itheima.web;

import javax.servlet.*;
import javax.servlet.annotation.WebServlet;
import java.io.IOException;

/**
 * Servlet方法介绍
 */
@WebServlet(urlPatterns = "/demo3",loadOnStartup = 1)
public class ServletDemo3 implements Servlet {

    private ServletConfig servletConfig;
    /**
     *  初始化方法
     *  1.调用时机：默认情况下，Servlet被第一次访问时，调用
     *      * loadOnStartup: 默认为-1，修改为0或者正整数，则会在服务器启动的时候，调用
     *  2.调用次数: 1次
     * @param config
     * @throws ServletException
     */
    public void init(ServletConfig config) throws ServletException {
        this.servletConfig = config;
        System.out.println("init...");
    }
    public ServletConfig getServletConfig() {
        return servletConfig;
    }
    
    /**
     * 提供服务
     * 1.调用时机:每一次Servlet被访问时，调用
     * 2.调用次数: 多次
     * @param req
     * @param res
     * @throws ServletException
     * @throws IOException
     */
    public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
        System.out.println("servlet hello world~");
    }

    /**
     * 销毁方法
     * 1.调用时机：内存释放或者服务器关闭的时候，Servlet对象会被销毁，调用
     * 2.调用次数: 1次
     */
    public void destroy() {
        System.out.println("destroy...");
    }
    
    public String getServletInfo() {
        return "";
    }
}
```

getServletInfo()和getServletConfig()这两个方法使用的不是很多，大家了解下。

### 4.6 体系结构

通过上面的学习，我们知道要想编写一个Servlet就必须要实现Servlet接口，重写接口中的5个方法，虽然已经能完成要求，但是编写起来还是比较麻烦的，因为我们更关注的其实只有service方法，那有没有更简单方式来创建Servlet呢?

要想解决上面的问题，我们需要先对Servlet的体系结构进行下了解:

![1627240593506](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627240593506.png)

因为我们将来开发B/S架构的web项目，都是针对HTTP协议，所以我们自定义Servlet,会通过继承==HttpServlet==

具体的编写格式如下:

```java
@WebServlet("/demo4")
public class ServletDemo4 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //TODO GET 请求方式处理逻辑
        System.out.println("get...");
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //TODO Post 请求方式处理逻辑
        System.out.println("post...");
    }
}
```

* 要想发送一个GET请求，请求该Servlet，只需要通过浏览器发送`http://localhost:8080/web-demo/demo4`,就能看到doGet方法被执行了
* 要想发送一个POST请求，请求该Servlet，单单通过浏览器是无法实现的，这个时候就需要编写一个form表单来发送请求，在webapp下创建一个`a.html`页面，内容如下:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <form action="/web-demo/demo4" method="post">
        <input name="username"/><input type="submit"/>
    </form>
</body>
</html>
```

启动测试，即可看到doPost方法被执行了。

Servlet的简化编写就介绍完了，接着需要思考两个问题:

1. HttpServlet中为什么要根据请求方式的不同，调用不同的方法?
2. 如何调用?

针对问题一，我们需要回顾之前的知识点==前端发送GET和POST请求的时候，参数的位置不一致，GET请求参数在请求行中，POST请求参数在请求体中==，为了能处理不同的请求方式，我们得在service方法中进行判断，然后写不同的业务处理，这样能实现，但是每个Servlet类中都将有相似的代码，针对这个问题，有什么可以优化的策略么?

```java
package com.itheima.web;

import javax.servlet.*;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;


@WebServlet("/demo5")
public class ServletDemo5 implements Servlet {

    public void init(ServletConfig config) throws ServletException {

    }

    public ServletConfig getServletConfig() {
        return null;
    }

    public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
        //如何调用?
        //获取请求方式，根据不同的请求方式进行不同的业务处理
        HttpServletRequest request = (HttpServletRequest)req;
       //1. 获取请求方式
        String method = request.getMethod();
        //2. 判断
        if("GET".equals(method)){
            // get方式的处理逻辑
        }else if("POST".equals(method)){
            // post方式的处理逻辑
        }
    }

    public String getServletInfo() {
        return null;
    }

    public void destroy() {

    }
}

```

要解决上述问题，我们可以对Servlet接口进行继承封装，来简化代码开发。

```java
package com.itheima.web;

import javax.servlet.*;
import javax.servlet.http.HttpServletRequest;
import java.io.IOException;

public class MyHttpServlet implements Servlet {
    public void init(ServletConfig config) throws ServletException {

    }

    public ServletConfig getServletConfig() {
        return null;
    }

    public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
        HttpServletRequest request = (HttpServletRequest)req;
        //1. 获取请求方式
        String method = request.getMethod();
        //2. 判断
        if("GET".equals(method)){
            // get方式的处理逻辑
            doGet(req,res);
        }else if("POST".equals(method)){
            // post方式的处理逻辑
            doPost(req,res);
        }
    }

    protected void doPost(ServletRequest req, ServletResponse res) {
    }

    protected void doGet(ServletRequest req, ServletResponse res) {
    }

    public String getServletInfo() {
        return null;
    }

    public void destroy() {

    }
}

```

有了MyHttpServlet这个类，以后我们再编写Servlet类的时候，只需要继承MyHttpServlet，重写父类中的doGet和doPost方法，就可以用来处理GET和POST请求的业务逻辑。接下来，可以把ServletDemo5代码进行改造

```java
@WebServlet("/demo5")
public class ServletDemo5 extends MyHttpServlet {

    @Override
    protected void doGet(ServletRequest req, ServletResponse res) {
        System.out.println("get...");
    }

    @Override
    protected void doPost(ServletRequest req, ServletResponse res) {
        System.out.println("post...");
    }
}

```

将来页面发送的是GET请求，则会进入到doGet方法中进行执行，如果是POST请求，则进入到doPost方法。这样代码在编写的时候就相对来说更加简单快捷。

类似MyHttpServlet这样的类Servlet中已经为我们提供好了，就是HttpServlet,翻开源码，大家可以搜索`service()`方法，你会发现HttpServlet做的事更多，不仅可以处理GET和POST还可以处理其他五种请求方式。

```java
protected void service(HttpServletRequest req, HttpServletResponse resp)
        throws ServletException, IOException
    {
        String method = req.getMethod();

        if (method.equals(METHOD_GET)) {
            long lastModified = getLastModified(req);
            if (lastModified == -1) {
                // servlet doesn't support if-modified-since, no reason
                // to go through further expensive logic
                doGet(req, resp);
            } else {
                long ifModifiedSince = req.getDateHeader(HEADER_IFMODSINCE);
                if (ifModifiedSince < lastModified) {
                    // If the servlet mod time is later, call doGet()
                    // Round down to the nearest second for a proper compare
                    // A ifModifiedSince of -1 will always be less
                    maybeSetLastModified(resp, lastModified);
                    doGet(req, resp);
                } else {
                    resp.setStatus(HttpServletResponse.SC_NOT_MODIFIED);
                }
            }

        } else if (method.equals(METHOD_HEAD)) {
            long lastModified = getLastModified(req);
            maybeSetLastModified(resp, lastModified);
            doHead(req, resp);

        } else if (method.equals(METHOD_POST)) {
            doPost(req, resp);
            
        } else if (method.equals(METHOD_PUT)) {
            doPut(req, resp);
            
        } else if (method.equals(METHOD_DELETE)) {
            doDelete(req, resp);
            
        } else if (method.equals(METHOD_OPTIONS)) {
            doOptions(req,resp);
            
        } else if (method.equals(METHOD_TRACE)) {
            doTrace(req,resp);
            
        } else {
            //
            // Note that this means NO servlet supports whatever
            // method was requested, anywhere on this server.
            //

            String errMsg = lStrings.getString("http.method_not_implemented");
            Object[] errArgs = new Object[1];
            errArgs[0] = method;
            errMsg = MessageFormat.format(errMsg, errArgs);
            
            resp.sendError(HttpServletResponse.SC_NOT_IMPLEMENTED, errMsg);
        }
    }
```

**小结**

通过这一节的学习，要掌握:

1. HttpServlet的使用步骤

> 继承HttpServlet
>
> 重写doGet和doPost方法

2. HttpServlet原理

> 获取请求方式，并根据不同的请求方式，调用不同的doXxx方法

### 4.7 urlPattern配置

Servlet类编写好后，要想被访问到，就需要配置其访问路径（==urlPattern==）

* 一个Servlet,可以配置多个urlPattern

  ![1627272805178](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627272805178.png)

  ```java
  package com.itheima.web;
  
  import javax.servlet.ServletRequest;
  import javax.servlet.ServletResponse;
  import javax.servlet.annotation.WebServlet;
  
  /**
  * urlPattern: 一个Servlet可以配置多个访问路径
  */
  @WebServlet(urlPatterns = {"/demo7","/demo8"})
  public class ServletDemo7 extends MyHttpServlet {
  
      @Override
      protected void doGet(ServletRequest req, ServletResponse res) {
          
          System.out.println("demo7 get...");
      }
      @Override
      protected void doPost(ServletRequest req, ServletResponse res) {
      }
  }
  ```

  在浏览器上输入`http://localhost:8080/web-demo/demo7`,`http://localhost:8080/web-demo/demo8`这两个地址都能访问到ServletDemo7的doGet方法。

* ==urlPattern配置规则==

  * 精确匹配

    ![1627273174144](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627273174144.png)

    ```java
    /**
     * UrlPattern:
     * * 精确匹配
     */
    @WebServlet(urlPatterns = "/user/select")
    public class ServletDemo8 extends MyHttpServlet {
    
        @Override
        protected void doGet(ServletRequest req, ServletResponse res) {
    
            System.out.println("demo8 get...");
        }
        @Override
        protected void doPost(ServletRequest req, ServletResponse res) {
        }
    }
    ```

    访问路径`http://localhost:8080/web-demo/user/select`

  * 目录匹配

    ![1627273184095](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627273184095.png)

    ```java
    package com.itheima.web;
    
    import javax.servlet.ServletRequest;
    import javax.servlet.ServletResponse;
    import javax.servlet.annotation.WebServlet;
    
    /**
     * UrlPattern:
     * * 目录匹配: /user/*
     */
    @WebServlet(urlPatterns = "/user/*")
    public class ServletDemo9 extends MyHttpServlet {
    
        @Override
        protected void doGet(ServletRequest req, ServletResponse res) {
    
            System.out.println("demo9 get...");
        }
        @Override
        protected void doPost(ServletRequest req, ServletResponse res) {
        }
    }
    ```

    访问路径`http://localhost:8080/web-demo/user/任意`

    ==思考:==

    1. 访问路径`http://localhost:8080/web-demo/user`是否能访问到demo9的doGet方法?
    2. 访问路径`http://localhost:8080/web-demo/user/a/b`是否能访问到demo9的doGet方法?
    3. 访问路径`http://localhost:8080/web-demo/user/select`是否能访问到demo9还是demo8的doGet方法?

    答案是: 能、能、demo8，进而我们可以得到的结论是`/user/*`中的`/*`代表的是零或多个层级访问目录同时精确匹配优先级要高于目录匹配。

  * 扩展名匹配

    ![1627273194118](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627273194118.png)

    ```java
    package com.itheima.web;
    
    import javax.servlet.ServletRequest;
    import javax.servlet.ServletResponse;
    import javax.servlet.annotation.WebServlet;
    
    /**
     * UrlPattern:
     * * 扩展名匹配: *.do
     */
    @WebServlet(urlPatterns = "*.do")
    public class ServletDemo10 extends MyHttpServlet {
    
        @Override
        protected void doGet(ServletRequest req, ServletResponse res) {
    
            System.out.println("demo10 get...");
        }
        @Override
        protected void doPost(ServletRequest req, ServletResponse res) {
        }
    }
    ```

    访问路径`http://localhost:8080/web-demo/任意.do`

    ==注意==:

    1. 如果路径配置的不是扩展名，那么在路径的前面就必须要加`/`否则会报错

    ![1627274483755](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627274483755.png)

    2. 如果路径配置的是`*.do`,那么在*.do的前面不能加`/`,否则会报错

    ![1627274368245](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627274368245.png)

  * 任意匹配

    ![1627273201370](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1627273201370.png)

    ```java
    package com.itheima.web;
    
    import javax.servlet.ServletRequest;
    import javax.servlet.ServletResponse;
    import javax.servlet.annotation.WebServlet;
    
    /**
     * UrlPattern:
     * * 任意匹配： /
     */
    @WebServlet(urlPatterns = "/")
    public class ServletDemo11 extends MyHttpServlet {
    
        @Override
        protected void doGet(ServletRequest req, ServletResponse res) {
    
            System.out.println("demo11 get...");
        }
        @Override
        protected void doPost(ServletRequest req, ServletResponse res) {
        }
    }
    ```

    访问路径`http://localhost:8080/demo-web/任意`

    ```java
    package com.itheima.web;
    
    import javax.servlet.ServletRequest;
    import javax.servlet.ServletResponse;
    import javax.servlet.annotation.WebServlet;
    
    /**
     * UrlPattern:
     * * 任意匹配： /*
     */
    @WebServlet(urlPatterns = "/*")
    public class ServletDemo12 extends MyHttpServlet {
    
        @Override
        protected void doGet(ServletRequest req, ServletResponse res) {
    
            System.out.println("demo12 get...");
        }
        @Override
        protected void doPost(ServletRequest req, ServletResponse res) {
        }
    }
    
    ```

    访问路径`http://localhost:8080/demo-web/任意

    ==注意:==`/`和`/*`的区别?

    1. 当我们的项目中的Servlet配置了 "/",会覆盖掉tomcat中的DefaultServlet,当其他的url-pattern都匹配不上时都会走这个Servlet

    2. 当我们的项目中配置了"/*",意味着匹配任意访问路径

    3. DefaultServlet是用来处理静态资源，如果配置了"/"会把默认的覆盖掉，就会引发请求静态资源的时候没有走默认的而是走了自定义的Servlet类，**最终导致静态资源不能被访问**

**小结**

1. urlPattern总共有四种配置方式，分别是精确匹配、目录匹配、扩展名匹配、任意匹配

2. 五种配置的优先级为 精确匹配 > 目录匹配> 扩展名匹配 > /* > / ,无需记，以最终运行结果为准。

### 4.8 XML配置（一般只用注解）

前面对应Servlet的配置，我们都使用的是@WebServlet,这个是Servlet从3.0版本后开始支持注解配置，3.0版本前只支持XML配置文件的配置方法。

对于XML的配置步骤有两步:

* 编写Servlet类

```java
package com.itheima.web;

import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.annotation.WebServlet;

public class ServletDemo13 extends MyHttpServlet {

    @Override
    protected void doGet(ServletRequest req, ServletResponse res) {

        System.out.println("demo13 get...");
    }
    @Override
    protected void doPost(ServletRequest req, ServletResponse res) {
    }
}
```

* 在web.xml中配置该Servlet

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    
    
    
    <!-- 
        Servlet 全类名
    -->
    <servlet>
        <!-- servlet的名称，名字任意-->
        <servlet-name>demo13</servlet-name>
        <!--servlet的类全名-->
        <servlet-class>com.itheima.web.ServletDemo13</servlet-class>
    </servlet>

    <!-- 
        Servlet 访问路径
    -->
    <servlet-mapping>
        <!-- servlet的名称，要和上面的名称一致-->
        <servlet-name>demo13</servlet-name>
        <!-- servlet的访问路径-->
        <url-pattern>/demo13</url-pattern>
    </servlet-mapping>
</web-app>
```

这种配置方式和注解比起来，确认麻烦很多，所以建议大家使用注解来开发。但是大家要认识上面这种配置方式，因为并不是所有的项目都是基于注解开发的。



##Request&Response

**今日目标**

>* 掌握Request对象的概念与使用
>* 掌握Response对象的概念与使用
>* 能够完成用户登录注册案例的实现
>* 能够完成SqlSessionFactory工具类的抽取

## 1.Request和Response的概述

==Request是请求对象，Response是响应对象。==这两个对象在我们使用Servlet的时候有看到：![1628735216156](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628735216156.png)

此时，我们就需要思考一个问题request和response这两个参数的作用是什么?

![1628735746602](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628735746602.png)

* request:==获取==请求数据
  * 浏览器会发送HTTP请求到后台服务器[Tomcat]
  * HTTP的请求中会包含很多请求数据[请求行+请求头+请求体]
  * 后台服务器[Tomcat]会对HTTP请求中的数据进行解析并把解析结果存入到一个对象中
  * 所存入的对象即为request对象，所以我们可以从request对象中获取请求的相关参数
  * 获取到数据后就可以继续后续的业务，比如获取用户名和密码就可以实现登录操作的相关业务
* response:==设置==响应数据
  * 业务处理完后，后台就需要给前端返回业务处理的结果即响应数据
  * 把响应数据封装到response对象中
  * 后台服务器[Tomcat]会解析response对象,按照[响应行+响应头+响应体]格式拼接结果
  * 浏览器最终解析结果，把内容展示在浏览器给用户浏览

对于上述所讲的内容，我们通过一个案例来初步体验下request和response对象的使用。

```java
@WebServlet("/demo3")
public class ServletDemo3 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //使用request对象 获取请求数据
        String name = request.getParameter("name");//url?name=zhangsan

        //使用response对象 设置响应数据
        response.setHeader("content-type","text/html;charset=utf-8");
        response.getWriter().write("<h1>"+name+",欢迎您！</h1>");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("Post...");
    }
}
```

启动成功后就可以通过浏览器来访问，并且根据传入参数的不同就可以在页面上展示不同的内容:

![1628738273049](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628738273049.png)

**小结**

在这节中，我们主要认识了下request对象和reponse对象:

* request对象是用来封装请求数据的对象
* response对象是用来封装响应数据的对象

目前我们只知道这两个对象是用来干什么的，那么它们具体是如何实现的，就需要我们继续深入的学习。接下来，就先从Request对象来学习,主要学习下面这些内容:

* request继承体系

* request获取请求参数
* request请求转发

## 2. Request对象

### 2.1 Request继承体系

在学习这节内容之前，我们先思考一个问题，前面在介绍Request和Reponse对象的时候，比较细心的同学可能已经发现：

* 当我们的Servlet类实现的是Servlet接口的时候，service方法中的参数是ServletRequest和ServletResponse
* 当我们的Servlet类继承的是HttpServlet类的时候，doGet和doPost方法中的参数就变成HttpServletRequest和HttpServletReponse

那么，

* ServletRequest和HttpServletRequest的关系是什么?
* request对象是有谁来创建的?
* request提供了哪些API,这些API从哪里查?

首先，我们先来看下Request的继承体系:

![1628740441008](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628740441008.png)

从上图中可以看出，ServletRequest和HttpServletRequest都是Java提供的，所以我们可以打开JavaEE提供的API文档[参考: 资料/JavaEE7-api.chm],打开后可以看到:

![1628741839475](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628741839475.png)

所以ServletRequest和HttpServletRequest是继承关系，并且两个都是接口，接口是无法创建对象，这个时候就引发了下面这个问题:

![1628742224589](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628742224589.png)

这个时候，我们就需要用到Request继承体系中的`RequestFacade`:

* 该类实现了HttpServletRequest接口，也间接实现了ServletRequest接口。
* Servlet类中的service方法、doGet方法或者是doPost方法最终都是由Web服务器[Tomcat]来调用的，所以Tomcat提供了方法参数接口的具体实现类，并完成了对象的创建
* 要想了解RequestFacade中都提供了哪些方法，我们可以直接查看JavaEE的API文档中关于ServletRequest和HttpServletRequest的接口文档，因为RequestFacade实现了其接口就需要重写接口中的方法

对于上述结论，要想验证，可以编写一个Servlet，在方法中把request对象打印下，就能看到最终的对象是不是RequestFacade,代码如下:

```java
@WebServlet("/demo2")
public class ServletDemo2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println(request);
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    }
}
```

启动服务器，运行访问`http://localhost:8080/request-demo/demo2`,得到运行结果:

![1628743040046](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628743040046.png)

**小结**

* Request的继承体系为ServletRequest-->HttpServletRequest-->RequestFacade
* Tomcat需要解析请求数据，封装为request对象,并且创建request对象传递到service方法
* 使用request对象，可以查阅JavaEE API文档的HttpServletRequest接口中方法说明

### 2.2 Request获取请求数据

HTTP请求数据总共分为三部分内容，分别是==请求行、请求头、请求体==，对于这三部分内容的数据，分别该如何获取，首先我们先来学习请求行数据如何获取?

#### 2.2.1 获取请求行数据

请求行包含三块内容，分别是`请求方式`、`请求资源路径`、`HTTP协议及版本`

![1628748240075](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628748240075.png)

对于这三部分内容，request对象都提供了对应的API方法来获取，具体如下:

* 获取请求方式: `GET`

```
String getMethod()
```

* 获取虚拟目录(项目访问路径): `/request-demo`

```
String getContextPath()
```

* 获取URL(统一资源定位符): `http://localhost:8080/request-demo/req1`

```
StringBuffer getRequestURL()
```

* 获取URI(统一资源标识符): `/request-demo/req1`

```
String getRequestURI()
```

* 获取请求参数(GET方式): `username=zhangsan&password=123`

```
String getQueryString()
```

介绍完上述方法后，咱们通过代码把上述方法都使用下:

```java
/**
 * request 获取请求数据
 */
@WebServlet("/req1")
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // String getMethod()：获取请求方式： GET
        String method = req.getMethod();
        System.out.println(method);//GET
        // String getContextPath()：获取虚拟目录(项目访问路径)：/request-demo
        String contextPath = req.getContextPath();
        System.out.println(contextPath);
        // StringBuffer getRequestURL(): 获取URL(统一资源定位符)：http://localhost:8080/request-demo/req1
        StringBuffer url = req.getRequestURL();
        System.out.println(url.toString());
        // String getRequestURI()：获取URI(统一资源标识符)： /request-demo/req1
        String uri = req.getRequestURI();
        System.out.println(uri);
        // String getQueryString()：获取请求参数（GET方式）： username=zhangsan
        String queryString = req.getQueryString();
        System.out.println(queryString);
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
}
```

启动服务器，访问`http://localhost:8080/request-demo/req1?username=zhangsan&passwrod=123`，获取的结果如下:

![1628762794935](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628762794935.png)

#### 2.2.2 获取请求头数据

对于请求头的数据，格式为`key: value`如下:

![1628768652535](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628768652535.png)

所以根据请求头名称获取对应值的方法为:

```
String getHeader(String name)
```

接下来，在代码中如果想要获取客户端浏览器的版本信息，则可以使用

```java
/**
 * request 获取请求数据
 */
@WebServlet("/req1")
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求头: user-agent: 浏览器的版本信息
        String agent = req.getHeader("user-agent");
		System.out.println(agent);
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
}

```

重新启动服务器后，`http://localhost:8080/request-demo/req1?username=zhangsan&passwrod=123`，获取的结果如下:

![1628769145524](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628769145524.png)

#### 2.2.3 获取请求体数据

浏览器在发送GET请求的时候是没有请求体的，所以需要把请求方式变更为POST，请求体中的数据格式如下:

![1628768665185](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628768665185.png)

对于请求体中的数据，Request对象提供了如下两种方式来获取其中的数据，分别是:

* 获取字节输入流，如果前端发送的是字节数据，比如传递的是文件数据，则使用该方法

```
ServletInputStream getInputStream()
该方法可以获取字节
```

* 获取字符输入流，如果前端发送的是纯文本数据，则使用该方法

```
BufferedReader getReader()
```

接下来，大家需要思考，要想获取到请求体的内容该如何实现?

>具体实现的步骤如下:
>
>1.准备一个页面，在页面中添加form表单,用来发送post请求
>
>2.在Servlet的doPost方法中获取请求体数据
>
>3.在doPost方法中使用request的getReader()或者getInputStream()来获取
>
>4.访问测试

1. 在项目的webapp目录下添加一个html页面，名称为：`req.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<!-- 
    action:form表单提交的请求地址
    method:请求方式，指定为post
-->
<form action="/request-demo/req1" method="post">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit">
</form>
</body>
</html>
```

2. 在Servlet的doPost方法中获取数据

```java
/**
 * request 获取请求数据
 */
@WebServlet("/req1")
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //在此处获取请求体中的数据
    }
}
```

3. 调用getReader()或者getInputStream()方法，因为目前前端传递的是纯文本数据，所以我们采用getReader()方法来获取

```java
/**
 * request 获取请求数据
 */
@WebServlet("/req1")
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
         //获取post 请求体：请求参数
        //1. 获取字符输入流
        BufferedReader br = req.getReader();
        //2. 读取数据
        String line = br.readLine();
        System.out.println(line);
    }
}
```

==注意==

BufferedReader流是通过request对象来获取的，当请求完成后request对象就会被销毁，request对象被销毁后，BufferedReader流就会自动关闭，所以此处就不需要手动关闭流了。

4. 启动服务器，通过浏览器访问`http://localhost:8080/request-demo/req.html`

![1628770516387](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628770516387.png)

点击`提交`按钮后，就可以在控制台看到前端所发送的请求数据

![1628770585480](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628770585480.png)

**小结**

HTTP请求数据中包含了`请求行`、`请求头`和`请求体`，针对这三部分内容，Request对象都提供了对应的API方法来获取对应的值:

* 请求行
  * getMethod()获取请求方式
  * getContextPath()获取项目访问路径
  * getRequestURL()获取请求URL
  * getRequestURI()获取请求URI
  * getQueryString()获取GET请求方式的请求参数
* 请求头
  * getHeader(String name)根据请求头名称获取其对应的值
* 请求体
  * 注意: ==浏览器发送的POST请求才有请求体==
  * 如果是纯文本数据:getReader()
  * 如果是字节数据如文件数据:getInputStream()

#### 2.2.4 获取请求参数的通用方式

在学习下面内容之前，我们先提出两个问题:

* 什么是请求参数?
* 请求参数和请求数据的关系是什么?

1.什么是请求参数?

为了能更好的回答上述两个问题，我们拿用户登录的例子来说明

1.1 想要登录网址，需要进入登录页面

1.2 在登录页面输入用户名和密码

1.3 将用户名和密码提交到后台

1.4 后台校验用户名和密码是否正确

1.5 如果正确，则正常登录，如果不正确，则提示用户名或密码错误

上述例子中，用户名和密码其实就是我们所说的请求参数。

2.什么是请求数据?

请求数据则是包含请求行、请求头和请求体的所有数据

3.请求参数和请求数据的关系是什么?

3.1 请求参数是请求数据中的部分内容

3.2 如果是GET请求，请求参数在请求行中

3.3 如果是POST请求，请求参数一般在请求体中

对于请求参数的获取,常用的有以下两种:

* GET方式:

```
String getQueryString()
```

* POST方式:

```
BufferedReader getReader();
```

有了上述的知识储备，我们来实现一个案例需求:

（1）发送一个GET请求并携带用户名，后台接收后打印到控制台

（2）发送一个POST请求并携带用户名，后台接收后打印到控制台

此处大家需要注意的是GET请求和POST请求接收参数的方式不一样，具体实现的代码如下:

```java
@WebServlet("/req1")
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

        String result = req.getQueryString();
        System.out.println(result);

    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        BufferedReader br = req.getReader();
        String result = br.readLine();
        System.out.println(result);
    }
}
```

* 对于上述的代码，会存在什么问题呢?

![1628776252445](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628776252445.png)

* 如何解决上述重复代码的问题呢?

![1628776433318](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628776433318.png)

当然，也可以在doGet中调用doPost,在doPost中完成参数的获取和打印,另外需要注意的是，doGet和doPost方法都必须存在，不能删除任意一个。

==GET请求和POST请求获取请求参数的方式不一样，在获取请求参数这块该如何实现呢?==

要想实现，我们就需要==思考==:

GET请求方式和POST请求方式区别主要在于获取请求参数的方式不一样，是否可以提供一种==统一==获取请求参数的方式，从而==统一==doGet和doPost方法内的代码?

解决方案一:

```java
@WebServlet("/req1")
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求方式
        String method = req.getMethod();
        //获取请求参数
        String params = "";
        if("GET".equals(method)){
            params = req.getQueryString();
        }else if("POST".equals(method)){
            BufferedReader reader = req.getReader();
            params = reader.readLine();
        }
        //将请求参数进行打印控制台
        System.out.println(params);
      
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req,resp);
    }
}
```

使用request的getMethod()来获取请求方式，根据请求方式的不同分别获取请求参数值，这样就可以解决上述问题，但是以后每个Servlet都需要这样写代码，实现起来比较麻烦，这种方案我们不采用

解决方案二:

request对象已经将上述获取请求参数的方法进行了封装，并且request提供的方法实现的功能更强大，以后只需要调用request提供的方法即可，在request的方法中都实现了哪些操作?

(1)根据不同的请求方式获取请求参数，获取的内容如下:

![1628778931277](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628778931277.png)

(2)把获取到的内容进行分割，内容如下:

![1628779067793](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628779067793.png)

(3)把分割后端数据，存入到一个Map集合中:

![1628779368501](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628779368501.png)

**注意**:因为参数的值可能是一个，也可能有多个，所以Map的值的类型为String数组。

基于上述理论，request对象为我们提供了如下方法:

* 获取所有参数Map集合

```
Map<String,String[]> getParameterMap()
```

* 根据名称获取参数值（数组）

```
String[] getParameterValues(String name)
```

* 根据名称获取参数值(单个值)

```
String getParameter(String name)
```

接下来，我们通过案例来把上述的三个方法进行实例演示:

1.修改req.html页面，添加爱好选项，爱好可以同时选多个

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<form action="/request-demo/req2" method="get">
    <input type="text" name="username"><br>
    <input type="password" name="password"><br>
    <input type="checkbox" name="hobby" value="1"> 游泳
    <input type="checkbox" name="hobby" value="2"> 爬山 <br>
    <input type="submit">

</form>
</body>
</html>
```

![1628780937599](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628780937599.png)

2.在Servlet代码中获取页面传递GET请求的参数值

 2.1获取GET方式的所有请求参数

```java
/**
 * request 通用方式获取请求参数
 */
@WebServlet("/req2")
public class RequestDemo2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //GET请求逻辑
        System.out.println("get....");
        //1. 获取所有参数的Map集合
        Map<String, String[]> map = req.getParameterMap();
        for (String key : map.keySet()) {
            // username:zhangsan lisi
            System.out.print(key+":");

            //获取值
            String[] values = map.get(key);
            for (String value : values) {
                System.out.print(value + " ");
            }

            System.out.println();
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
}
```

获取的结果为:

![1628780965283](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628780965283.png)

 2.2获取GET请求参数中的爱好，结果是数组值

```java
/**
 * request 通用方式获取请求参数
 */
@WebServlet("/req2")
public class RequestDemo2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //GET请求逻辑
        //...
        System.out.println("------------");
        String[] hobbies = req.getParameterValues("hobby");
        for (String hobby : hobbies) {
            System.out.println(hobby);
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
}
```

获取的结果为:

![1628781031437](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628781031437.png)

 2.3获取GET请求参数中的用户名和密码，结果是单个值

```java
/**
 * request 通用方式获取请求参数
 */
@WebServlet("/req2")
public class RequestDemo2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //GET请求逻辑
        //...
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        System.out.println(username);
        System.out.println(password);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
    }
}
```

获取的结果为:

![1628781176434](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628781176434.png)

3.在Servlet代码中获取页面传递POST请求的参数值

 3.1将req.html页面form表单的提交方式改成post

 3.2将doGet方法中的内容复制到doPost方法中即可

**小结**

* req.getParameter()方法使用的频率会比较高

* 以后我们再写代码的时候，就只需要按照如下格式来编写:

```
public class RequestDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
       //采用request提供的获取请求参数的通用方式来获取请求参数
       //编写其他的业务代码...
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req,resp);
    }
}
```

### 2.3 IDEA快速创建Servlet

使用通用方式获取请求参数后，屏蔽了GET和POST的请求方式代码的不同，则代码可以定义如下格式:

![1628781419752](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628781419752.png)

由于格式固定，所以我们可以使用IDEA提供的模板来制作一个Servlet的模板，这样我们后期在创建Servlet的时候就会更高效，具体如何实现:

(1)按照自己的需求，修改Servlet创建的模板内容

![1628781545912](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628781545912.png)

（2）使用servlet模板创建Servlet类

![1628782117420](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628782117420.png)

### 2.4 请求参数中文乱码问题

问题展示:

(1)将req.html页面的请求方式修改为get

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<form action="/request-demo/req2" method="get">
    <input type="text" name="username"><br>
    <input type="password" name="password"><br>
    <input type="checkbox" name="hobby" value="1"> 游泳
    <input type="checkbox" name="hobby" value="2"> 爬山 <br>
    <input type="submit">

</form>
</body>
</html>
```

(2)在Servlet方法中获取参数，并打印

```java
/**
 * 中文乱码问题解决方案
 */
@WebServlet("/req4")
public class RequestDemo4 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
       //1. 获取username
       String username = request.getParameter("username");
       System.out.println(username);
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

（3）启动服务器，页面上输入中文参数

![1628784323297](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628784323297.png)

（4）查看控制台打印内容

![1628784356157](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628784356157.png)

（5）把req.html页面的请求方式改成post,再次发送请求和中文参数

![1628784425182](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628784425182.png)

（6）查看控制台打印内容，依然为乱码

![1628784356157](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628784356157.png)

通过上面的案例，会发现，不管是GET还是POST请求，在发送的请求参数中如果有中文，在后台接收的时候，都会出现中文乱码的问题。具体该如何解决呢？

#### 2.4.1 POST请求解决方案

* 分析出现中文乱码的原因：
  * POST的请求参数是通过request的getReader()来获取流中的数据
  * TOMCAT在获取流的时候采用的编码是ISO-8859-1
  * ISO-8859-1编码是不支持中文的，所以会出现乱码
* 解决方案：
  * 页面设置的编码格式为UTF-8
  * 把TOMCAT在获取流数据之前的编码设置为UTF-8
  * 通过request.setCharacterEncoding("UTF-8")设置编码,UTF-8也可以写成小写

修改后的代码为:

```java
/**
 * 中文乱码问题解决方案
 */
@WebServlet("/req4")
public class RequestDemo4 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1. 解决乱码: POST getReader()
        //设置字符输入流的编码，设置的字符集要和页面保持一致
        request.setCharacterEncoding("UTF-8");
       //2. 获取username
       String username = request.getParameter("username");
       System.out.println(username);
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

重新发送POST请求，就会在控制台看到正常展示的中文结果。

至此POST请求中文乱码的问题就已经解决，但是这种方案不适用于GET请求，这个原因是什么呢，咱们下面再分析。

#### 2.4.2 GET请求解决方案

刚才提到一个问题是`POST请求的中文乱码解决方案为什么不适用GET请求？`

* GET请求获取请求参数的方式是`request.getQueryString()`
* POST请求获取请求参数的方式是`request.getReader()`
* request.setCharacterEncoding("utf-8")是设置request处理流的编码
* getQueryString方法并没有通过流的方式获取数据

所以GET请求不能用设置编码的方式来解决中文乱码问题，那问题又来了，如何解决GET请求的中文乱码呢? 

1. 首先我们需要先分析下GET请求出现乱码的原因:

 ![1628829610823](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628829610823.png)

(1)浏览器通过HTTP协议发送请求和数据给后台服务器（Tomcat)

(2)浏览器在发送HTTP的过程中会对中文数据进行URL==编码==

(3)在进行URL编码的时候会采用页面`<meta>`标签指定的UTF-8的方式进行编码，`张三`编码后的结果为`%E5%BC%A0%E4%B8%89`

(4)后台服务器(Tomcat)接收到`%E5%BC%A0%E4%B8%89`后会默认按照`ISO-8859-1`进行URL==解码==

(5)由于前后编码与解码采用的格式不一样，就会导致后台获取到的数据为乱码。

思考: 如果把`req.html`页面的`<meta>`标签的charset属性改成`ISO-8859-1`,后台不做操作，能解决中文乱码问题么?

答案是否定的，因为`ISO-8859-1`本身是不支持中文展示的，所以改了<meta>标签的charset属性后，会导致页面上的中文内容都无法正常展示。

分析完上面的问题后，我们会发现，其中有两个我们不熟悉的内容就是==URL编码==和==URL解码==，什么是URL编码，什么又是URL解码呢?

**URL编码**

这块知识我们只需要了解下即可,具体编码过程分两步，分别是:

(1)将字符串按照编码方式转为二进制

(2)每个字节转为2个16进制数并在前边加上%

`张三`按照UTF-8的方式转换成二进制的结果为:

```
1110 0101 1011 1100 1010 0000 1110 0100 1011 1000 1000 1001
```

这个结果是如何计算的?

使用`http://www.mytju.com/classcode/tools/encode_utf8.asp`，输入`张三`

![1628833310473](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628833310473.png)

就可以获取张和三分别对应的10进制，然后在使用计算器，选择程序员模式，计算出对应的二进制数据结果:

![1628833496171](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628833496171.png)

在计算的十六进制结果中，每两位前面加一个%,就可以获取到`%E5%BC%A0%E4%B8%89`。

当然你从上面所提供的网站中就已经能看到编码16进制的结果了:

![1628833310473](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628833310474.png)

但是对于上面的计算过程，如果没有工具，纯手工计算的话，相对来说还是比较复杂的，我们也不需要进行手动计算，在Java中已经为我们提供了编码和解码的API工具类可以让我们更快速的进行编码和解码:

编码:

```java
java.net.URLEncoder.encode("需要被编码的内容","字符集(UTF-8)")
```

解码:

```java
java.net.URLDecoder.decode("需要被解码的内容","字符集(UTF-8)")
```

接下来咱们对`张三`来进行编码和解码

```
public class URLDemo {

  public static void main(String[] args) throws UnsupportedEncodingException {
        String username = "张三";
        //1. URL编码
        String encode = URLEncoder.encode(username, "utf-8");
        System.out.println(encode); //打印:%E5%BC%A0%E4%B8%89

       //2. URL解码
       //String decode = URLDecoder.decode(encode, "utf-8");//打印:张三
       String decode = URLDecoder.decode(encode, "ISO-8859-1");//打印:`å¼ ä¸ `
       System.out.println(decode);
    }
}

```

到这，我们就可以分析出GET请求中文参数出现乱码的原因了，

* 浏览器把中文参数按照`UTF-8`进行URL编码
* Tomcat对获取到的内容进行了`ISO-8859-1`的URL解码
* 在控制台就会出现类上`å¼ ä¸`的乱码，最后一位是个空格

2. 清楚了出现乱码的原因，接下来我们就需要想办法进行解决

![1628846824194](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628846824194.png)

从上图可以看住，

* 在进行编码和解码的时候，不管使用的是哪个字符集，他们对应的`%E5%BC%A0%E4%B8%89`是一致的

* 那他们对应的二进制值也是一样的，为:

  * ```
    1110 0101 1011 1100 1010 0000 1110 0100 1011 1000 1000 1001
    ```

* 为所以我们可以考虑把`å¼ ä¸`转换成字节，在把字节转换成`张三`，在转换的过程中是它们的编码一致，就可以解决中文乱码问题。

具体的实现步骤为:

>1.按照ISO-8859-1编码获取乱码`å¼ ä¸`对应的字节数组
>
>2.按照UTF-8编码获取字节数组对应的字符串

实现代码如下:

```
public class URLDemo {

  public static void main(String[] args) throws UnsupportedEncodingException {
        String username = "张三";
        //1. URL编码
        String encode = URLEncoder.encode(username, "utf-8");
        System.out.println(encode);
        //2. URL解码
        String decode = URLDecoder.decode(encode, "ISO-8859-1");

        System.out.println(decode); //此处打印的是对应的乱码数据

        //3. 转换为字节数据,编码
        byte[] bytes = decode.getBytes("ISO-8859-1");
        for (byte b : bytes) {
            System.out.print(b + " ");
        }
		//此处打印的是:-27 -68 -96 -28 -72 -119
        //4. 将字节数组转为字符串，解码
        String s = new String(bytes, "utf-8");
        System.out.println(s); //此处打印的是张三
    }
}
```

**说明**:在第18行中打印的数据是`-27 -68 -96 -28 -72 -119`和`张三`转换成的二进制数据`1110 0101 1011 1100 1010 0000 1110 0100 1011 1000 1000 1001`为什么不一样呢？

其实打印出来的是十进制数据，我们只需要使用计算机换算下就能得到他们的对应关系，如下图:

![1628849231208](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628849231208.png)

至此对于GET请求中文乱码的解决方案，我们就已经分析完了，最后在代码中去实现下:

```java
/**
 * 中文乱码问题解决方案
 */
@WebServlet("/req4")
public class RequestDemo4 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1. 解决乱码：POST，getReader()
        //request.setCharacterEncoding("UTF-8");//设置字符输入流的编码

        //2. 获取username
        String username = request.getParameter("username");
        System.out.println("解决乱码前："+username);

        //3. GET,获取参数的方式：getQueryString
        // 乱码原因：tomcat进行URL解码，默认的字符集ISO-8859-1
       /* //3.1 先对乱码数据进行编码：转为字节数组
        byte[] bytes = username.getBytes(StandardCharsets.ISO_8859_1);
        //3.2 字节数组解码
        username = new String(bytes, StandardCharsets.UTF_8);*/

        username  = new String(username.getBytes(StandardCharsets.ISO_8859_1),StandardCharsets.UTF_8);

        System.out.println("解决乱码后："+username);

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

**注意**

* 把`request.setCharacterEncoding("UTF-8")`代码注释掉后，会发现GET请求参数乱码解决方案同时也可也把POST请求参数乱码的问题也解决了
* 只不过对于POST请求参数一般都会比较多，采用这种方式解决乱码起来比较麻烦，所以对于POST请求还是建议使用设置编码的方式进行。

另外需要说明一点的是==Tomcat8.0之后，已将GET请求乱码问题解决，设置默认的解码方式为UTF-8==

**小结**

1. 中文乱码解决方案

* POST请求和GET请求的参数中如果有中文，后台接收数据就会出现中文乱码问题

  GET请求在Tomcat8.0以后的版本就不会出现了

* POST请求解决方案是:设置输入流的编码

  ```
  request.setCharacterEncoding("UTF-8");
  注意:设置的字符集要和页面保持一致
  ```

* 通用方式（GET/POST）：需要先解码，再编码

  ```
  new String(username.getBytes("ISO-8859-1"),"UTF-8");
  ```

2. URL编码实现方式:

* 编码:

  ```
  URLEncoder.encode(str,"UTF-8");
  ```

* 解码:

  ```
  URLDecoder.decode(s,"ISO-8859-1");
  ```

### 2.5 Request请求转发

1. ==请求转发(forward):一种在服务器内部的资源跳转方式。==

![1628851404283](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628851404283.png)

(1)浏览器发送请求给服务器，服务器中对应的资源A接收到请求

(2)资源A处理完请求后将请求发给资源B

(3)资源B处理完后将结果响应给浏览器

(4)请求从资源A到资源B的过程就叫==请求转发==

2. 请求转发的实现方式:

```
req.getRequestDispatcher("资源B路径").forward(req,resp);
```

具体如何来使用，我们先来看下需求:

![1628854783523](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628854783523.png)

针对上述需求，具体的实现步骤为:

>1.创建一个RequestDemo5类，接收/req5的请求，在doGet方法中打印`demo5`
>
>2.创建一个RequestDemo6类，接收/req6的请求，在doGet方法中打印`demo6`
>
>3.在RequestDemo5的方法中使用
>
>​	req.getRequestDispatcher("/req6").forward(req,resp)进行请求转发
>
>4.启动测试

(1)创建RequestDemo5类

```java
/**
 * 请求转发
 */
@WebServlet("/req5")
public class RequestDemo5 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("demo5...");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(2)创建RequestDemo6类

```java
/**
 * 请求转发
 */
@WebServlet("/req6")
public class RequestDemo6 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("demo6...");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(3)在RequestDemo5的doGet方法中进行请求转发

```java
/**
 * 请求转发
 */
@WebServlet("/req5")
public class RequestDemo5 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("demo5...");
        //请求转发
        request.getRequestDispatcher("/req6").forward(request,response);
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(4)启动测试

访问`http://localhost:8080/request-demo/req5`,就可以在控制台看到如下内容:

![1628855192876](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628855192876.png)

说明请求已经转发到了`/req6`

3. 请求转发资源间共享数据:使用Request对象

此处主要解决的问题是把请求从`/req5`转发到`/req6`的时候，如何传递数据给`/req6`。

需要使用request对象提供的三个方法:

* 存储数据到request域[范围,数据是存储在request对象]中

```
void setAttribute(String name,Object o);
```

* 根据key获取值

```
Object getAttribute(String name);
```

* 根据key删除该键值对

```
void removeAttribute(String name);
```

接着上个需求来:

![1628856995417](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628856995417.png)

> 1.在RequestDemo5的doGet方法中转发请求之前，将数据存入request域对象中
>
> 2.在RequestDemo6的doGet方法从request域对象中获取数据，并将数据打印到控制台
>
> 3.启动访问测试

(1)修改RequestDemo5中的方法

```java
@WebServlet("/req5")
public class RequestDemo5 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("demo5...");
        //存储数据
        request.setAttribute("msg","hello");
        //请求转发
        request.getRequestDispatcher("/req6").forward(request,response);

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(2)修改RequestDemo6中的方法

```java
/**
 * 请求转发
 */
@WebServlet("/req6")
public class RequestDemo6 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("demo6...");
        //获取数据
        Object msg = request.getAttribute("msg");
        System.out.println(msg);

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(3)启动测试

访问`http://localhost:8080/request-demo/req5`,就可以在控制台看到如下内容:

![1628857213364](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628857213364.png)

此时就可以实现在转发多个资源之间共享数据。

4. 请求转发的特点

* 浏览器地址栏路径不发生变化

  虽然后台从`/req5`转发到`/req6`,但是浏览器的地址一直是`/req5`,未发生变化

  ![1628857365153](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628857365153.png)

* 只能转发到当前服务器的内部资源

  不能从一个服务器通过转发访问另一台服务器

* 一次请求，可以在转发资源间使用request共享数据

  虽然后台从`/req5`转发到`/req6`，但是这个==只有一次请求==

## 3，Response对象

前面讲解完Request对象，接下来我们回到刚开始的那张图:

![1628857632899](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628857632899.png)

* Request:使用request对象来==获取==请求数据
* Response:使用response对象来==设置==响应数据

Reponse的继承体系和Request的继承体系也非常相似:

![1628857761317](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628857761317.png)

 介绍完Response的相关体系结构后，接下来对于Response我们需要学习如下内容:

* Response设置响应数据的功能介绍
* Response完成重定向
* Response响应字符数据
* Response响应字节数据

### 3.1 Response设置响应数据功能介绍

HTTP响应数据总共分为三部分内容，分别是==响应行、响应头、响应体==，对于这三部分内容的数据，respone对象都提供了哪些方法来进行设置?

1. 响应行

![1628858926498](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628858926498.png)

对于响应头，比较常用的就是设置响应状态码:

```
void setStatus(int sc);
```

2. 响应头

![1628859051368](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628859051368.png)

设置响应头键值对：

```
void setHeader(String name,String value);
```

3. 响应体

![1628859268095](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628859268095.png)

对于响应体，是通过字符、字节输出流的方式往浏览器写，

获取字符输出流:

```
PrintWriter getWriter();
```

获取字节输出流

```
ServletOutputStream getOutputStream();
```

介绍完这些方法后，后面我们会通过案例把这些方法都用一用，首先先来完成下重定向的功能开发。

### 3.2 Respones请求重定向

1. ==Response重定向(redirect):一种资源跳转方式。==

![1628859860279](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628859860279.png)

(1)浏览器发送请求给服务器，服务器中对应的资源A接收到请求

(2)资源A现在无法处理该请求，就会给浏览器响应一个302的状态码+location的一个访问资源B的路径

(3)浏览器接收到响应状态码为302就会重新发送请求到location对应的访问地址去访问资源B

(4)资源B接收到请求后进行处理并最终给浏览器响应结果，这整个过程就叫==重定向==

2. 重定向的实现方式:

```
resp.setStatus(302);
resp.setHeader("location","资源B的访问路径");
```

具体如何来使用，我们先来看下需求:

![1628861030429](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628861030429.png)

针对上述需求，具体的实现步骤为:

> 1.创建一个ResponseDemo1类，接收/resp1的请求，在doGet方法中打印`resp1....`
>
> 2.创建一个ResponseDemo2类，接收/resp2的请求，在doGet方法中打印`resp2....`
>
> 3.在ResponseDemo1的方法中使用
>
> ​	response.setStatus(302);
>
> ​	response.setHeader("Location","/request-demo/resp2") 来给前端响应结果数据
>
> 4.启动测试

(1)创建ResponseDemo1类

```java
@WebServlet("/resp1")
public class ResponseDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("resp1....");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(2)创建ResponseDemo2类

```java
@WebServlet("/resp2")
public class ResponseDemo2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("resp2....");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(3)在ResponseDemo1的doGet方法中给前端响应数据

```java
@WebServlet("/resp1")
public class ResponseDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("resp1....");
        //重定向
        //1.设置响应状态码 302
        response.setStatus(302);
        //2. 设置响应头 Location
        response.setHeader("Location","/request-demo/resp2");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

(4)启动测试

访问`http://localhost:8080/request-demo/resp1`,就可以在控制台看到如下内容:

![1628861404699](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628861404699.png)

说明`/resp1`和`/resp2`都被访问到了。到这重定向就已经完成了。

虽然功能已经实现，但是从设置重定向的两行代码来看，会发现除了重定向的地址不一样，其他的内容都是一模一样，所以request对象给我们提供了简化的编写方式为:

```
resposne.sendRedirect("/request-demo/resp2")
```

所以第3步中的代码就可以简化为：

```java
@WebServlet("/resp1")
public class ResponseDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("resp1....");
        //重定向
        resposne.sendRedirect("/request-demo/resp2")；
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

3. 重定向的特点

* 浏览器地址栏路径发送变化

  当进行重定向访问的时候，由于是由浏览器发送的两次请求，所以地址会发生变化

  ![1628861893130](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628861893130.png)

* 可以重定向到任何位置的资源(服务内容、外部均可)

  因为第一次响应结果中包含了浏览器下次要跳转的路径，所以这个路径是可以任意位置资源。

* 两次请求，不能在多个资源使用request共享数据

  因为浏览器发送了两次请求，是两个不同的request对象，就无法通过request对象进行共享数据

介绍完==请求重定向==和==请求转发==以后，接下来需要把这两个放在一块对比下:

![1628862170296](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628862170296.png)

以后到底用哪个，还是需要根据具体的业务来决定。

### 3.3 路径问题

1. 问题1：转发的时候路径上没有加`/request-demo`而重定向加了，那么到底什么时候需要加，什么时候不需要加呢?

![1628862652700](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628862652700.png)

其实判断的依据很简单，只需要记住下面的规则即可:

* 浏览器使用:需要加虚拟目录(项目访问路径)
* 服务端使用:不需要加虚拟目录

对于转发来说，因为是在服务端进行的，所以不需要加虚拟目录

对于重定向来说，路径最终是由浏览器来发送请求，就需要添加虚拟目录。

掌握了这个规则，接下来就通过一些练习来强化下知识的学习:

* `<a href='路劲'>`
* `<form action='路径'>`
* req.getRequestDispatcher("路径")
* resp.sendRedirect("路径")

答案:

```
1.超链接，从浏览器发送，需要加
2.表单，从浏览器发送，需要加
3.转发，是从服务器内部跳转，不需要加
4.重定向，是由浏览器进行跳转，需要加。
```

2. 问题2：在重定向的代码中，`/request-demo`是固定编码的，如果后期通过Tomcat插件配置了项目的访问路径，那么所有需要重定向的地方都需要重新修改，该如何优化?

![1628863270545](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628863270545.png)

答案也比较简单，我们可以在代码中动态去获取项目访问的虚拟目录，具体如何获取，我们可以借助前面咱们所学习的request对象中的getContextPath()方法，修改后的代码如下:

```java
@WebServlet("/resp1")
public class ResponseDemo1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("resp1....");

        //简化方式完成重定向
        //动态获取虚拟目录
        String contextPath = request.getContextPath();
        response.sendRedirect(contextPath+"/resp2");
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

重新启动访问测试，功能依然能够实现，此时就可以动态获取项目访问的虚拟路径，从而降低代码的耦合度。

### 3.4 Response响应字符数据

要想将字符数据写回到浏览器，我们需要两个步骤:

* 通过Response对象获取字符输出流： PrintWriter writer = resp.getWriter();

* 通过字符输出流写数据: writer.write("aaa");

接下来，我们实现通过些案例把响应字符数据给实际应用下:

1. 返回一个简单的字符串`aaa`

```java
/**
 * 响应字符数据：设置字符数据的响应体
 */
@WebServlet("/resp3")
public class ResponseDemo3 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html;charset=utf-8");
        //1. 获取字符输出流
        PrintWriter writer = response.getWriter();
		 writer.write("aaa");
    }
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

![1628863905362](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628863905362.png)

2. 返回一串html字符串，并且能被浏览器解析

```
PrintWriter writer = response.getWriter();
//content-type，告诉浏览器返回的数据类型是HTML类型数据，这样浏览器才会解析HTML标签
response.setHeader("content-type","text/html");
writer.write("<h1>aaa</h1>");
```

![1628864140820](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628864140820.png)

==注意:==一次请求响应结束后，response对象就会被销毁掉，所以不要手动关闭流。

3. 返回一个中文的字符串`你好`，需要注意设置响应数据的编码为`utf-8`

```
//设置响应的数据格式及数据的编码
response.setContentType("text/html;charset=utf-8");
writer.write("你好");
```

![1628864390263](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628864390263.png)

### 3.3 Response响应字节数据

要想将字节数据写回到浏览器，我们需要两个步骤:

- 通过Response对象获取字节输出流：ServletOutputStream outputStream = resp.getOutputStream();

- 通过字节输出流写数据: outputStream.write(字节数据);

接下来，我们实现通过些案例把响应字符数据给实际应用下:

1. 返回一个图片文件到浏览器

```java
/**
 * 响应字节数据：设置字节数据的响应体
 */
@WebServlet("/resp4")
public class ResponseDemo4 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1. 读取文件
        FileInputStream fis = new FileInputStream("d://a.jpg");
        //2. 获取response字节输出流
        ServletOutputStream os = response.getOutputStream();
        //3. 完成流的copy
        byte[] buff = new byte[1024];
        int len = 0;
        while ((len = fis.read(buff))!= -1){
            os.write(buff,0,len);
        }
        fis.close();
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

![1628864883564](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628864883564.png)

上述代码中，对于流的copy的代码还是比较复杂的，所以我们可以使用别人提供好的方法来简化代码的开发，具体的步骤是:

(1)pom.xml添加依赖

```xml
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.6</version>
</dependency>
```

(2)调用工具类方法

```
//fis:输入流
//os:输出流
IOUtils.copy(fis,os);
```

优化后的代码:

```java
/**
 * 响应字节数据：设置字节数据的响应体
 */
@WebServlet("/resp4")
public class ResponseDemo4 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1. 读取文件
        FileInputStream fis = new FileInputStream("d://a.jpg");
        //2. 获取response字节输出流
        ServletOutputStream os = response.getOutputStream();
        //3. 完成流的copy
      	IOUtils.copy(fis,os);
        fis.close();
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

## 4，用户注册登录案例

接下来我们通过两个比较常见的案例，一个是==注册==，一个是==登录==来对今天学习的内容进行一个实战演练，首先来实现用户登录。

### 4.1 用户登录

#### 4.1.1 需求分析

![1628865728305](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628865728305.png)

1. 用户在登录页面输入用户名和密码，提交请求给LoginServlet
2. 在LoginServlet中接收请求和数据[用户名和密码]
3. 在LoginServlt中通过Mybatis实现调用UserMapper来根据用户名和密码查询数据库表
4. 将查询的结果封装到User对象中进行返回
5. 在LoginServlet中判断返回的User对象是否为null
6. 如果为nul，说明根据用户名和密码没有查询到用户，则登录失败，返回"登录失败"数据给前端
7. 如果不为null,则说明用户存在并且密码正确，则登录成功，返回"登录成功"数据给前端

#### 4.1.2 环境准备

1. 复制资料中的静态页面到项目的webapp目录下

参考`资料\1. 登陆注册案例\1. 静态页面`,拷贝完效果如下:

![1628866248169](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628866248169.png)

2. 创建db1数据库，创建tb_user表，创建User实体类

2.1 将`资料\1. 登陆注册案例\2. MyBatis环境\tb_user.sql`中的sql语句执行下:

![1628866403891](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628866403891.png)

 2.2 将`资料\1. 登陆注册案例\2. MyBatis环境\User.java`拷贝到com.itheima.pojo

![1628866560738](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628866560738.png)

3. 在项目的pom.xml导入Mybatis和Mysql驱动坐标

```xml
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.5.5</version>
</dependency>

<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.34</version>
</dependency>
```

4. 创建mybatis-config.xml核心配置文件，UserMapper.xml映射文件,UserMapper接口

4.1  将`资料\1. 登陆注册案例\2. MyBatis环境\mybatis-config.xml`拷贝到resources目录下

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!--起别名-->
    <typeAliases>
        <package name="com.itheima.pojo"/>
    </typeAliases>

    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <!--
                    useSSL:关闭SSL安全连接 性能更高
                    useServerPrepStmts:开启预编译功能
                    &amp; 等同于 & ,xml配置文件中不能直接写 &符号
                -->
                <property name="url" value="jdbc:mysql:///db1?useSSL=false&amp;useServerPrepStmts=true"/>
                <property name="username" value="root"/>
                <property name="password" value="1234"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <!--扫描mapper-->
        <package name="com.itheima.mapper"/>
    </mappers>
</configuration>
```

4.2 在com.itheima.mapper包下创建UserMapper接口

```java
public interface UserMapper {

}
```

4.3 将`资料\1. 登陆注册案例\2. MyBatis环境\UserMapper.xml`拷贝到resources目录下

==注意：在resources下创建UserMapper.xml的目录时，要使用/分割==

![1628867237329](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628867237329.png)

至此我们所需要的环境就都已经准备好了，具体该如何实现?

#### 4.1.3 代码实现

1. 在UserMapper接口中提供一个根据用户名和密码查询用户对象的方法

```java
/**
     * 根据用户名和密码查询用户对象
     * @param username
     * @param password
     * @return
     */
    @Select("select * from tb_user where username = #{username} and password = #{password}")
    User select(@Param("username") String username,@Param("password")  String password);
```

**说明**

@Param注解的作用:用于传递参数,是方法的参数可以与SQL中的字段名相对应。

2. 修改loign.html

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>login</title>
    <link href="css/login.css" rel="stylesheet">
</head>

<body>
<div id="loginDiv">
    <form action="/request-demo/loginServlet" method="post" id="form">
        <h1 id="loginMsg">LOGIN IN</h1>
        <p>Username:<input id="username" name="username" type="text"></p>

        <p>Password:<input id="password" name="password" type="password"></p>

        <div id="subDiv">
            <input type="submit" class="button" value="login up">
            <input type="reset" class="button" value="reset">&nbsp;&nbsp;&nbsp;
            <a href="register.html">没有账号？点击注册</a>
        </div>
    </form>
</div>

</body>
</html>
```

3. 编写LoginServlet

```java
@WebServlet("/loginServlet")
public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1. 接收用户名和密码
        String username = request.getParameter("username");
        String password = request.getParameter("password");

        //2. 调用MyBatis完成查询
        //2.1 获取SqlSessionFactory对象
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.2 获取SqlSession对象
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //2.3 获取Mapper
        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
        //2.4 调用方法
        User user = userMapper.select(username, password);
        //2.5 释放资源
        sqlSession.close();


        //获取字符输出流，并设置content type
        response.setContentType("text/html;charset=utf-8");
        PrintWriter writer = response.getWriter();
        //3. 判断user释放为null
        if(user != null){
            // 登陆成功
            writer.write("登陆成功");
        }else {
            // 登陆失败
            writer.write("登陆失败");
        }
    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

4. 启动服务器测试

4.1 如果用户名和密码输入错误，则

![1628867761245](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628867761245.png)

4.2 如果用户名和密码输入正确，则

![1628867801708](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628867801708.png)

至此用户的登录功能就已经完成了~

### 4.2 用户注册

#### 4.2.1 需求分析

![1628867904783](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/1628867904783.png)

1. 用户在注册页面输入用户名和密码，提交请求给RegisterServlet
2. 在RegisterServlet中接收请求和数据[用户名和密码]
3. 在RegisterServlet中通过Mybatis实现调用UserMapper来根据用户名查询数据库表
4. 将查询的结果封装到User对象中进行返回
5. 在RegisterServlet中判断返回的User对象是否为null
6. 如果为nul，说明根据用户名可用，则调用UserMapper来实现添加用户
7. 如果不为null,则说明用户不可以，返回"用户名已存在"数据给前端

#### 4.2.2 代码编写

1. 编写UserMapper提供根据用户名查询用户数据方法和添加用户方法

```java
/**
* 根据用户名查询用户对象
* @param username
* @return
*/
@Select("select * from tb_user where username = #{username}")
User selectByUsername(String username);

/**
* 添加用户
* @param user
*/
@Insert("insert into tb_user values(null,#{username},#{password})")
void add(User user);
```

2. 修改register.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>欢迎注册</title>
    <link href="css/register.css" rel="stylesheet">
</head>
<body>

<div class="form-div">
    <div class="reg-content">
        <h1>欢迎注册</h1>
        <span>已有帐号？</span> <a href="login.html">登录</a>
    </div>
    <form id="reg-form" action="/request-demo/registerServlet" method="post">

        <table>

            <tr>
                <td>用户名</td>
                <td class="inputs">
                    <input name="username" type="text" id="username">
                    <br>
                    <span id="username_err" class="err_msg" style="display: none">用户名不太受欢迎</span>
                </td>

            </tr>

            <tr>
                <td>密码</td>
                <td class="inputs">
                    <input name="password" type="password" id="password">
                    <br>
                    <span id="password_err" class="err_msg" style="display: none">密码格式有误</span>
                </td>
            </tr>

        </table>

        <div class="buttons">
            <input value="注 册" type="submit" id="reg_btn">
        </div>
        <br class="clear">
    </form>

</div>
</body>
</html>
```

3. 创建RegisterServlet类

```java
@WebServlet("/registerServlet")
public class RegisterServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //1. 接收用户数据
        String username = request.getParameter("username");
        String password = request.getParameter("password");

        //封装用户对象
        User user = new User();
        user.setUsername(username);
        user.setPassword(password);

        //2. 调用mapper 根据用户名查询用户对象
        //2.1 获取SqlSessionFactory对象
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.2 获取SqlSession对象
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //2.3 获取Mapper
        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);

        //2.4 调用方法
        User u = userMapper.selectByUsername(username);

        //3. 判断用户对象释放为null
        if( u == null){
            // 用户名不存在，添加用户
            userMapper.add(user);

            // 提交事务
            sqlSession.commit();
            // 释放资源
            sqlSession.close();
        }else {
            // 用户名存在，给出提示信息
            response.setContentType("text/html;charset=utf-8");
            response.getWriter().write("用户名已存在");
        }

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doGet(request, response);
    }
}
```

4. 启动服务器进行测试

4.1 如果测试成功，则在数据库中就能查看到新注册的数据

4.2 如果用户已经存在，则在页面上展示 `用户名已存在` 的提示信息

### 4.3 SqlSessionFactory工具类抽取

上面两个功能已经实现，但是在写Servlet的时候，因为需要使用Mybatis来完成数据库的操作，所以对于Mybatis的基础操作就出现了些重复代码，如下

```java
String resource = "mybatis-config.xml";
InputStream inputStream = Resources.getResourceAsStream(resource);
SqlSessionFactory sqlSessionFactory = new 
	SqlSessionFactoryBuilder().build(inputStream);
```

有了这些重复代码就会造成一些问题:

* 重复代码不利于后期的维护
* SqlSessionFactory工厂类进行重复创建
  * 就相当于每次买手机都需要重新创建一个手机生产工厂来给你制造一个手机一样，资源消耗非常大但性能却非常低。所以这么做是不允许的。

那如何来优化呢？

* 代码重复可以抽取工具类
* 对指定代码只需要执行一次可以使用静态代码块

有了这两个方向后，代码具体该如何编写?

```java
public class SqlSessionFactoryUtils {

    private static SqlSessionFactory sqlSessionFactory;

    static {
        //静态代码块会随着类的加载而自动执行，且只执行一次
        try {
            String resource = "mybatis-config.xml";
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }


    public static SqlSessionFactory getSqlSessionFactory(){
        return sqlSessionFactory;
    }
}
```

工具类抽取以后，以后在对Mybatis的SqlSession进行操作的时候，就可以直接使用

```java
SqlSessionFactory sqlSessionFactory =SqlSessionFactoryUtils.getSqlSessionFactory();
```

这样就可以很好的解决上面所说的代码重复和重复创建工厂导致性能低的问题了。三层架构目录

![image-20240321161253693](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20240321161253693.png)
