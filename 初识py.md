# 基本知识

![image-20230723140405767](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230723140405767.png)

## input

需要注意的是，input返回的是一个字符串，如果要用于赋值整形数据需要在接受的时候进行强制转换

## 变量

### 全局变量

在Python中，可以使用`global`关键字来声明一个变量为全局变量。这意味着该变量可以在程序的任何地方进行访问和修改，而不受局部作用域的限制。

以下是如何定义全局变量：

```python
global_var = 10  # 这是一个全局变量

def my_function():
    global global_var  # 声明要使用的全局变量
    global_var += 5  # 修改全局变量

# 调用函数，修改全局变量的值
my_function()

print(global_var)  # 输出修改后的全局变量值
```

在上面的例子中，我们首先定义了一个全局变量`global_var`，然后在`my_function`函数中使用`global`关键字将其声明为全局变量。在函数内部，我们可以对该全局变量进行修改。最后，我们打印出修改后的全局变量值。

![image-20230730200542923](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730200542923.png)

![image-20230730200701086](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730200701086.png)

对布尔值进行整形强制转换，非零的值都会被转换为1

![image-20230727113603681](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230727113603681.png)

## 运算符

浮点型保留的位数就是运算过程中最大的小数位置

![image-20230730210109375](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730210109375.png)



![image-20230730202319857](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730202319857.png)

比较有好的是，python中提供了大于等于，比c语言可人性多了

![image-20230730202434594](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730202434594.png)

### ord与chr

```python
a="A"
#如果直接print(int(a)),结果会报错
#需要用到ord函数
print(ord(a))
#也可以直接使用ord函数
print(ord('A'))
```

![image-20230730202518450](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730202518450.png)

还有一个按位运算符，感觉了解一下就好了

![image-20230730203135243](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730203135243.png)

### 成员运算符

`这个指定序列可以是字符串，列表或者元组，用来查找很方便`

![image-20230730203350358](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730203350358.png)



![image-20230730203211392](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730203211392.png)

### 身份运算符

目前还没用到，先了解一下

`这个是判断内存地址是否相同，不知道有什么用`

![image-20230730203421763](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730203421763.png)

![image-20230730203428187](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730203428187.png)

### 运算符的优先级

![image-20230730203527911](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730203527911.png)



**多了** // **

![img](file:///C:\Users\谢隆杰\AppData\Local\Temp\ksohtml25044\wps1.png)

or的优先级会更高，跟c语言||一样

![img](file:///C:\Users\谢隆杰\AppData\Local\Temp\ksohtml25044\wps2.jpg)

**成员运算符**

in

![image-20230728203306441](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230728203306441.png)

不能用来测试数字类型

## print

## *号收集多余的值，并且可以放在任意顺序

![image-20230816170729505](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816170729505.png)

*需要值得一提的是，带‘*’的变量返回的是一个列表*

###  格式字符串

#### 如何控制字符串宽度，精度和千分位隔符

在 Python 的 f-string 中，你可以使用格式化选项来控制字符串的宽度、精度以及千分位隔符。格式化选项使用冒号 `:` 后跟各种格式规范。

下面是一些示例：

1. **控制字符串宽度：** 你可以使用数字指定字段的最小宽度。如果字段内容不够宽度，将使用空格进行填充。

```python
text = "Hello"
formatted_text = f"|{text:10}|"
print(formatted_text)  # 输出：|Hello     |
```

2. **控制精度：** 对于浮点数，你可以使用 `.n` 格式规范来指定小数位数。例如，`.2f` 表示保留两位小数。

```python
value = 123.456789
formatted_value = f"Value: {value:.2f}"
print(formatted_value)  # 输出：Value: 123.46
```

3. **使用千分位隔符：** 对于整数或浮点数，你可以使用 `,` 来添加千分位隔符。

```python
number = 1234567
formatted_number = f"Formatted: {number:,}"
print(formatted_number)  # 输出：Formatted: 1,234,567
```

结合使用这些格式规范，你可以对字符串的宽度、精度和千分位隔符进行精确控制。例如：

```python
amount = 12345.6789
formatted_amount = f"Amount: {amount:,.2f}"
print(formatted_amount)  # 输出：Amount: 12,345.68
```

请注意，格式规范中的各种选项可以根据你的需求进行组合使用，以实现更复杂的格式化效果。

#### 两个浮点型变量相乘，怎样控制他的精度

你可以使用 `round()` 函数来控制两个浮点型变量相乘后的精度。`round()` 函数可以将一个浮点数四舍五入到指定的小数位数。

以下是一个示例：

```python
num1 = 3.1415926
num2 = 2.7182818

product = num1 * num2
rounded_product = round(product, 2)  # 将结果四舍五入保留两位小数

print(rounded_product)
```

在上面的示例中，`rounded_product` 将会是两个浮点数相乘并四舍五入到两位小数后的结果。

注意：由于浮点数在计算机内部表示时存在精度限制，可能会导致计算结果并不精确。如果需要更高精度的计算，可以考虑使用 `decimal` 模块，该模块提供了更精确的十进制浮点数运算。

#### 如何控制向左向右对其，还有补0这样的操作

在 Python 中，你可以使用字符串格式化操作来实现对齐和补零的操作。字符串格式化操作提供了多种方式来控制输出的对齐和填充。以下是一些示例：

**1. 左对齐、右对齐和居中对齐：**

你可以使用字符串格式化中的 `>`（右对齐）、`<`（左对齐）和 `^`（居中对齐）来控制对齐方式。

```python
text = "Hello"
print(f"{text:<10}")  # 左对齐，总宽度为 10
print(f"{text:>10}")  # 右对齐，总宽度为 10
print(f"{text:^10}")  # 居中对齐，总宽度为 10
```

**2. 补零：**

你可以在格式化字符串中使用 `0` 来指定补零操作。通常用于格式化数字。

```python
number = 42
print(f"{number:04}")  # 补零，总宽度为 4
```

**3. 混合对齐和补零：**

你可以将对齐和补零操作组合在一起。

```python
number = 123
print(f"{number:0>6}")  # 右对齐，总宽度为 6，补零
print(f"{number:0<6}")  # 左对齐，总宽度为 6，补零
```

这些示例演示了如何使用 f-string 来控制对齐和补零操作。你还可以使用其他字符串格式化方法，如 `.format()` 方法来实现类似的功能。根据你的需求，选择适合的方法即可。

```python
a,b=map(int,input().split())
print(f'''{a*b:.3f}''')
```



这里的print会自动换行

![image-20230729120557024](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729120557024.png)

![image-20230729120604616](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729120604616.png)

### 如果想直接打印换行

![image-20230729120803241](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729120803241.png)



## range

参数说明
![image-20230729120832104](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729120832104.png)

```python
# 生成从0到4之前的整数序列：[0, 1, 2, 3]
sequence1 = range(4)

# 生成从2到6之前的整数序列：[2, 3, 4, 5]
sequence2 = range(2, 6)

# 生成从1到10之前，步长为2的整数序列：[1, 3, 5, 7, 9]
sequence3 = range(1, 10, 2)

```

![image-20230729154851744](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729154851744.png)

## 练习

![image-20230729164235689](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729164235689.png)

生成一个随机的车牌号

![image-20230729164252753](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729164252753.png)

python第一枪

### 运用在练习的方法

#### join

![image-20230729164512123](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729164512123.png)

#### random.choice

![image-20230729164545998](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729164545998.png)

#### random.sample

![image-20230729164617252](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230729164617252.png)

**需要注意的是，他的返回值是一个列表**

# 数据结构

![image-20230731203144811](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731203144811.png)

- 序列

  - 字符串
  - 列表
  - 元组
  - unicode
  - 对象
  - xrange对象

- 映射

  - 自带你

    

![image-20230731203511022](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731203511022.png)

### 可变的数据类型

列表，字典，可变集合

### 不可变数据类型

python中的赋值是指向性赋值（我目前是这么理解），重新给一个数据赋值会把变量名指向另外的一个id地址，可以利用id()函数来辅助裂解

`数字，字符串，元组，不可变集合`



### 元组

- 元组不可变
- 不能对元组进行修改，增添等操作，属于不可变数据类型

#### 元组的创建

- 使用圆括号创建![image-20230731211128968](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731211128968.png)

**这一点中我觉得很牛逼的是不加圆括号也可以创建元组**

- 使用tuple函数创建

  ![image-20230731211506066](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731211506066.png)

  

#### 元组的提取和常用的函数和方法

- 直接索引提取

- 元组的切片提取

- 元组解包![image-20230731211753827](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731211753827.png)

  其中mytuple=('China','American','England')



![image-20230731212230402](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731212230402.png)

**这个方法与list和str相似**

## str

### split

`str.split(sep=None, maxsplit=-1)` 是字符串对象的一个方法，用于将字符串按照指定的分隔符（默认为空格）进行分割，并返回一个包含分割后子字符串的列表。函数原型如下：

- `sep`: 分隔符，可以是一个字符串或者 None。如果不指定分隔符，默认以空格进行分割。
- `maxsplit`: 可选参数，表示最大分割次数。默认为 -1，表示不限制分割次数。

使用示例：

```python
s = "Hello,world,how,are,you"

# 以逗号为分隔符进行分割
result = s.split(",")
print(result)  # Output: ['Hello', 'world', 'how', 'are', 'you']

# 以空格为分隔符进行分割
words = "This is a test"
word_list = words.split()
print(word_list)  # Output: ['This', 'is', 'a', 'test']

# 限制最大分割次数为2
text = "apple orange banana mango"
fruits = text.split(" ", 2)
print(fruits)  # Output: ['apple', 'orange', 'banana mango']
```

注意：`split` **方法返回一个列表**，其中包含分割后的子字符串。默认情况下，它会删除分隔符。如果希望保留分隔符，可以考虑使用正则表达式或其他方法。

### join

```python
>>> jn1="-"
>>> jn2="------"
>>> str='name'
>>> jn1.join(str)    #字符串也属于序列
'n-a-m-e'
>>> jn2.join(str)    #使用多字符连接序列
'n------a------m------e'
>>> fruits={'apple','banana'}
>>> jn1.join(fruits)   #连接的序列是集合
'apple-banana'
>>> animals=("pig","dog") 
>>> jn1.join(animals)   #连接的序列是元祖
'pig-dog'
>>> students={"name1":"joy","name2":"john","name3":"jerry"}   #连接的序列是字典，会将所有key连接起来
>>> jn1.join(students)
'name1-name2-name3'
```



### 拼接

![image-20230730201724246](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730201724246.png)



### 一些介绍



**字符串不可修改！**

![image-20230730201121096](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730201121096.png)

![image-20230730201238508](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730201238508.png)**尽量用双引号来表达字符串**

![image-20230730201514045](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730201514045.png)



**字符串的切片顾头不顾尾**

 ![image-20230730104304818](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730104304818.png)

很像char数组，但是不能单独该一个元素，只能重新定义，修改之后原来的状态会被视为垃圾，被回收，跟java的垃圾处理有点像

**常用的方法**

center

![image-20230730104610991](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730104610991.png)

![image-20230730104616150](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730104616150.png)

### count

![image-20230730104711902](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730104711902.png)

查找字符串中的某个元素个数，可以设置起始位置和结尾位置

![image-20230730110401417](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730110401417.png)



### find

#### find和In的差别

当涉及字符串存在判定时，使用 `in` 关键字和 `find()` 方法都是常见的方法，但它们在实现上有一些差别：

1. **使用 `in` 关键字：**
```python
if b in a:
    print('True')
else:
    print('False')
```

2. **使用 `find()` 方法：**
```python
if a.find(b) != -1:
    print('True')
else:
    print('False')
```

主要区别如下：

- **返回值：**
  - 使用 `in` 关键字：返回一个布尔值，表示是否找到了子字符串。
  - 使用 `find()` 方法：返回子字符串第一次出现的索引，如果未找到则返回 -1。

- **判断逻辑：**
  - 使用 `in` 关键字：直观地判断一个字符串是否包含另一个字符串，适用于只关心是否存在而不需要索引信息的情况。
  - 使用 `find()` 方法：可以得到子字符串在父字符串中的索引位置，适用于需要知道子字符串具体位置的情况。

- **速度：**
  - 通常情况下，`find()` 方法稍微比 `in` 关键字快一些，因为它只需要找到第一个匹配就可以停止搜索。而 `in` 关键字会继续搜索整个字符串，直到找到匹配或者遍历完整个字符串。

在大多数情况下，这两种方法的差别并不会对程序性能产生显著影响。您可以根据您的实际需求选择适合的方法。如果您只关心是否存在，使用 `in` 关键字会更加直观和简洁。如果您需要知道子字符串的索引位置，使用 `find()` 方法会更合适。

![image-20230730104930971](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730104930971.png)

如果找到了，就返回对应字符的索引，**返回的索引是字子串第一个字符的索引**

###isdigit

判断是不是整数，如果是字符串的整数也会返回true,否则返回false

### join

![image-20230730105118935](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730105118935.png)

![image-20230730105159536](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730105159536.png)

###replace

![image-20230730105333496](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730105333496.png)

注意这个

![image-20230730105417317](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730105417317.png)

*由于无法对字符串直接修改，所以需要重新定义*，如果有多个l，可以在后面指定要替换的个数，

### split![image-20230730105618491](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730105618491.png)



可以按照指定的标准分隔字符串为列表，不指定sep参数就是按照空格分隔

## list

### 列表的创建

![image-20230731204218262](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731204218262.png)



![image-20230731204412190](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731204412190.png)

列表的索引可以从最右边开始索引，最右边的索引为-1

**👇为列表的切片索引**



![image-20230731204926216](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731204926216.png)

![image-20230731205022245](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731205022245.png)



### len

**len(list)求列表的长度，元素个数，可以用于字符串以及dict**

### **extend**

![image-20230730110617555](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730110617555.png)

extend的效果与使用自增运算的效果相同

```python
mon=['shuai','ge']
one=['shi','wo']
mon.exend(one)
#效果上相同与
mon+=one
```

**列表可以嵌套链表，对列表的列表中元素的取值如下**

![image-20230730110715506](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730110715506.png)

### pop

list.pop(index)

直接删除列表最后的元素，并且返回被删除的值，也可以的指定删除的元素的index

### remove

与pop不同remove是通过元素的值来删除，pop是通过index来删除

### index（str）

返回的是对应元素的索引

![image-20230730111207933](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730111207933.png)

### 切片（与字符串类似）

![image-20230730111302543](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730111302543.png)

#### **切片还可以倒着切，可以应用于不知道正着数的Index**

![image-20230730112023834](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730112023834.png)

-5：-1就是倒数第五个倒倒数第一个



#### 跳着切

step是最后一个参数

![image-20230730112306281](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730112306281.png)







![image-20230730111442191](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730111442191.png)

### 排序和反转

#### sort

`sort()` 是 Python 列表的内置方法，用于对列表进行原地排序（在原列表上进行修改，而不是返回一个新列表）。`sort()` 方法可以按升序或降序对列表元素进行排序，默认是按升序排序。

`sort()` 方法的语法如下：

```python
list.sort(key=None, reverse=False)
```

其中，参数说明如下：

- `key`：可选参数，用于指定一个排序关键字函数，用于确定排序的依据。它是一个函数，接受列表中的每个元素作为参数，返回用于排序的值。如果不指定 `key`，默认使用列表元素本身进行比较排序。
- `reverse`：可选参数，是一个布尔值，用于指定排序顺序。如果设置为 `True`，则表示按降序排序（从大到小），如果设置为 `False`，则表示按升序排序（从小到大）。默认为 `False`。

下面是一些使用 `sort()` 方法的例子：

```python
# 按升序排序
numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5]
numbers.sort()
print(numbers)  # Output: [1, 1, 2, 3, 4, 5, 5, 6, 9]

# 按降序排序
numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5]
numbers.sort(reverse=True)
print(numbers)  # Output: [9, 6, 5, 5, 4, 3, 2, 1, 1]

# 使用 key 参数按字符串长度排序
words = ["apple", "orange", "banana", "kiwi"]
words.sort(key=len)
print(words)  # Output: ['kiwi', 'apple', 'banana', 'orange']
```

在使用 `sort()` 方法时，需要注意以下几点：

1. `sort()` 方法是原地排序，会修改原始列表，不会创建新列表。
2. 如果列表元素是不可比较的类型或不符合排序规则，会抛出 `TypeError`。
3. 对于复杂对象的排序，可以使用 `key` 参数指定排序依据，例如按照对象的某个属性进行排序。
4. 如果只需要排序的结果而不想修改原列表，可以使用 `sorted()` 函数，它会返回一个新的已排序的列表。

![image-20230730112653169](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730112653169.png)

##### 如果元素是列表

如果列表的元素是列表，我们仍然可以使用 `sort()` 方法对它们进行排序，但是需要指定一个排序关键字函数（`key` 参数），该函数返回一个用于比较排序的值。

在排序关键字函数中，我们可以使用元素的某个子元素作为排序依据，比如列表的第一个元素、第二个元素等。在 Python 中，对于可迭代对象（包括列表），可以使用索引访问元素。因此，如果要按照列表中的子列表的第一个元素进行排序，可以使用以下方法：

```python
# 示例：按照列表中的子列表的第一个元素进行排序
nested_list = [[3, 1], [1, 2], [2, 3], [1, 5], [2, 4]]
nested_list.sort(key=lambda x: x[0])

print(nested_list)
# Output: [[1, 2], [1, 5], [2, 3], [2, 4], [3, 1]]
```

在上面的示例中，我们使用了 `lambda x: x[0]` 作为排序关键字函数，这表示按照每个子列表的第一个元素进行排序。结果是按照第一个元素的升序进行了排序。

如果要按照子列表的其他元素进行排序，只需要修改 **`x[0]`** 中的索引即可，比如按照第二个元素进行排序，可以使用 **`lambda x: x[1]`**。

需要注意的是，排序关键字函数可以根据需求灵活地编写，它决定了按照哪个值进行排序。在实际应用中，根据需要来选择合适的排序关键字函数。

如果列表是纯数字

![image-20230730112744952](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730112744952.png)

#### reverse

反转列表

![image-20230730112853571](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730112853571.png)

### 循环列表

![image-20230730112911032](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730112911032.png)

### insert（index，元素）

![image-20230731205412688](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731205412688.png)

### 查询列表文件位置

![image-20230731210025726](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731210025726.png)

其他常用方法

![image-20230731210048493](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230731210048493.png)

### count

和str和tuple一样的用法



## dict

首先，字典属于`映射型`数据结构类型，没有索引的概念，也没有切片的操作

字典的索引直接搜key,value可以存放可以修改的数值，key不可以存放可以修改的数值，比如列表

![image-20230730143620625](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230730143620625.png)

![image-20230801193023531](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801193023531.png)同样可以用in判断元素是否在dict中

### 元素提取

![image-20230801193117358](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801193117358.png)

### 字典中常用的函数和方法

#### setdefault

`setdefault()` 是Python字典（`dict`）的一个方法，用于在字典中获取指定键的值，如果该键不存在，则将键值对添加到字典中。它的语法如下：

```python
dict.setdefault(key, default=None)
```

- `key`：要查找的键。
- `default`：如果键不存在，则设置键的默认值为该参数。

如果字典中已经存在给定的键，`setdefault()` 方法将返回键对应的值；如果键不存在，则会将键值对添加到字典中，并返回默认值（如果提供了）。这个方法可以方便地初始化字典中的键值对。

示例：

```python
my_dict = {'a': 1, 'b': 2}

value_a = my_dict.setdefault('a', 0)
value_c = my_dict.setdefault('c', 3)

print(my_dict)   # 输出: {'a': 1, 'b': 2, 'c': 3}
print(value_a)   # 输出: 1 (已存在的键)
print(value_c)   # 输出: 3 (新键，使用默认值)
```

在上面的示例中，`setdefault('a', 0)` 返回已存在的键 `'a'` 的值 `1`，而 `setdefault('c', 3)` 在字典中添加了新的键值对 `'c': 3`，并返回默认值 `3`。

需要注意的是，如果没有提供默认值，`setdefault()` 方法会将默认值设为 `None`。如果希望设置不同的默认值，可以在调用时传递对应的值作为参数。



####增加

#### ![image-20230801193441081](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801193441081.png)

直接添加，**键访问**，比较适合单个元素的添加

如果有多个元素，可以把多个元素放在一个新的字典，然后用update合并成一个新的字典，跟列表的extend类似

![image-20230801193657070](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801193657070.png)

***需要注意的是，如果有相同的key,新的Key会覆盖掉旧的Key中的内容***

#### 删除

- pop的通过key（列表中的索引）删除
- clear的全部删除
- del的通过key元素

![image-20230801194034653](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801194034653.png)

#### 修改

![image-20230801194104057](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801194104057.png)

直接修改

#### 查询

![image-20230801194220760](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801194220760.png)

三种方法，很重要

**使用示例**

![image-20230801194249009](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801194249009.png)

## 集合

![image-20230801195332895](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801195332895.png)

### 创建集合

#### 可变集合

```python
#代码 3-39 创建可变集合
\# 使用花括号创建可变集合
\>>> myset1={'A','C','D','B','A','B'} 
\>>> myset1 
{'C', 'D', 'B', 'A'} 
\# 使用函数 set 创建可变集合
\>>> myset2=set([2,3,1,4,False,2.5,'one']) 
\>>> myset2 
{False, 1, 2, 3, 4, 2.5, 'one'} 
\>>> empty_set=set() # 创建空可变集合
\>>> empty_set 
set() 
\>>> type(empty_set) 
<class 'set'> 
```

#### 不可变集合

![image-20230801195901351](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801195901351.png)

### 集合的运算

#### 求并集

- 直接使用'|'

- 使用union函数

  

```python
>>> A={'足球','游泳','羽毛球','乒乓球'} 
>>> B={'篮球','乒乓球','羽毛球','排球'} 
>>> A|B # 使用符号'|'获取并集
{'羽毛球', '排球', '乒乓球', '足球', '篮球', '游泳'} 
>>> A.union(B) # 使用集合方法 union 函数获取并集
{'羽毛球', '排球', '乒乓球', '足球', '篮球', '游泳'}
```

#### 求交集

![image-20230801200136214](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801200136214.png)

#### 求差集

![image-20230801200144237](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801200144237.png)

#### 异或集

![image-20230801200211961](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801200211961.png)

#### 集合之间的关系判断（了解，感觉用的不多）

![image-20230801200317554](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801200317554.png)

![image-20230801200322513](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801200322513.png)

### 集合中常用的函数和方法

![image-20230801201242842](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801201242842.png)

实例

![image-20230801201350070](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801201350070.png)

# 控制语句

## 列表循环

列表推导是一种从其他列表创建列表的方式，类似于数学中的集合推导。列表推导的工作原

理非常简单，有点类似于for循环。



```python
>>> [x * x for x in range(10)] 

[0, 1, 4, 9, 16, 25, 36, 49, 64, 81] 
```

可以在此基础上添加多重for,和if

![image-20230816184123490](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816184123490.png)



## 迭代工具

### 并行迭代

**可以运用到zip函数**

![image-20230816173013203](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816173013203.png)



## 链式比较

**c语言中不能使用这种比较**

![image-20230816172322559](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816172322559.png)





## is

<img src="C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816172003054.png" alt="image-20230816172003054" style="zoom:100%;" />



## if



这些都是假的值，其他都是真![image-20230816171422109](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816171422109.png)



![image-20230801203559434](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801203559434.png)

多路分支

![image-20230801203616513](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801203616513.png)



## for

![image-20230801204104181](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801204104181.png)

与其他语言不同的是这个pass

![image-20230801204152066](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801204152066.png)

不做任何事情

### 多变量迭代

只要是可迭代的数据类型都可以循环，无论有没有下标

![image-20230801204450479](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801204450479.png)

一次迭代多个变量

![image-20230801204553014](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801204553014.png)

### 创建列表解析

*map函数可以详见`一些实用的内置函数`*

![image-20230801204833030](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801204833030.png)

如代码 4-17 所示，列表解析式完全可以替换 Python 内建的 map 函数以及 lambda 函数，而且效率更高。用列表解析式实现嵌套循环语句的示例如代码 4-18 所示

![image-20230801204947533](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230801204947533.png)

**感觉有点酷的样子**



# 函数

## 自定义函数



- python的自定义函数可以不需声明数据类型

  ![image-20230802145210560](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230802145210560.png)

  

## 函数返回值

![image-20230804112622542](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804112622542.png)



## 函数参数

- 位置参数

- 关键字参数

  ​	![image-20230804112705613](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804112705613.png)关键字参数的关键字参数调用可以不用按照传入顺序调用

- 默认参数

  ​	在没有传入参数的时候可以有一个默认值![image-20230802154231137](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230802154231137.png)

  

- 可变参数

  **不确定的可变参数需要放在最后面**

- ![image-20230802154851245](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230802154851245.png)

  这个有点牛，相当于自动重载了函数

  
  
  ![image-20230804112749148](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804112749148.png)

## 匿名函数

### lambda

![image-20230804113330396](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804113330396.png)





## 一些实用的内置函数

### isinstance

`isinstance` 是一个内置函数，用于检查一个对象是否是指定类型或类的实例。它的语法是：

```python
isinstance(object, classinfo)
```

- `object` 是要检查的对象。
- `classinfo` 是一个类型、类或类型元组。

`isinstance` 返回一个布尔值，如果 `object` 是 `classinfo` 类型或类的实例（或其子类的实例），则返回 `True`，否则返回 `False`。

例如：

```python
class MyClass:
    pass

obj1 = MyClass()
print(isinstance(obj1, MyClass))  # 输出 True

obj2 = "Hello"
print(isinstance(obj2, MyClass))  # 输出 False
```

在这个示例中，`obj1` 是 `MyClass` 类的实例，因此 `isinstance(obj1, MyClass)` 返回 `True`。而 `obj2` 是字符串类型，不是 `MyClass` 类的实例，因此 `isinstance(obj2, MyClass)` 返回 `False`。

###  encode

```python
text = "Hello, 你好"
encoded_utf8 = text.encode('utf-8')
encoded_ascii = text.encode('ascii', errors='ignore')

print("UTF-8 Encoding:", encoded_utf8)
print("ASCII Encoding (with ignore):", encoded_ascii)
```



### sum

`sum()` 是 Python 内置函数之一，用于计算可迭代对象（如列表、元组等）中所有元素的总和。它接受一个可迭代对象作为参数，并返回所有元素的总和。

语法：
```python
sum(iterable, start=0)
```

参数：
- `iterable`：必需，表示要计算总和的可迭代对象，如列表、元组等。
- `start`：可选，表示起始值，默认为 0。如果提供了 `start` 参数，则 `sum()` 函数会在计算总和之前先加上 `start`。

返回值：
- 返回可迭代对象中所有元素的总和。

示例：
```python
numbers = [1, 2, 3, 4, 5]

# 计算列表中所有元素的总和
total_sum = sum(numbers)
print(total_sum)  # 输出: 15

# 可以指定一个起始值
total_sum_with_start = sum(numbers, 10)
print(total_sum_with_start)  # 输出: 25，等于 10 + 1 + 2 + 3 + 4 + 5
```

`sum()` 函数对于处理数值型的列表、元组等数据非常方便，可以快速计算出它们的总和。注意，当处理大量数据时，可能需要注意数值溢出的问题。

### round

`round()` 是 Python 内置函数之一，用于对一个数进行四舍五入的操作。它可以接受一个数值作为参数，并返回最接近该数值的整数。

语法：
```python
round(number, ndigits=None)
```

参数：
- `number`：必需，表示要进行四舍五入的数值。
- `ndigits`：可选，表示要保留的小数位数，默认为 `None`，即不指定保留小数位数，此时 `round()` 函数会返回一个整数。

返回值：
- 返回经过四舍五入后的数值，如果指定了 `ndigits`，则返回保留指定小数位数的数值。

示例：
```python
x = 3.14159

# 不指定保留小数位数，进行四舍五入，返回整数
rounded_int = round(x)
print(rounded_int)  # 输出: 3

# 指定保留2位小数
rounded_float = round(x, 2)
print(rounded_float)  # 输出: 3.14
```

在上面的示例中，`round()` 函数对数值 `x` 进行了四舍五入操作。在第一个例子中，由于没有指定保留小数位数，所以返回了一个整数。而在第二个例子中，我们指定保留2位小数，返回了一个保留2位小数的浮点数。

需要注意的是，`round()` 函数并不只能对小数进行四舍五入，它同样适用于整数，返回的结果将是一个整数。另外，`ndigits` 参数可以是负数，表示对整数位进行四舍五入。

### map（可以用解析式替代）

`map()` 是 Python 内置函数之一，它是一个高阶函数，用于将一个函数应用到可迭代对象的每个元素上，并返回一个结果迭代器。

语法：
```python
map(function, iterable, ...)
```

参数：
- `function`：必需，表示要应用的函数，可以是内置函数、自定义函数或 lambda 函数。
- `iterable`：必需，表示要处理的可迭代对象，如列表、元组等。`map()` 将会对 `iterable` 中的每个元素应用 `function`。
- `...`：可选，表示可以有多个可迭代对象作为参数，此时 `map()` 函数会将这些可迭代对象的对应元素作为参数传递给 `function`。

返回值：
- 返回一个迭代器，其中包含将 `function` 应用于 `iterable` 中每个元素后的结果,**注意是返回一个新的迭代器，不改变原来的**

示例：
```python
# 定义一个函数，将数字加倍
def double(x):
    return x * 2

numbers = [1, 2, 3, 4, 5]

# 使用 map() 将 double 函数应用于 numbers 列表的每个元素
result = map(double, numbers)

# result 是一个迭代器，我们可以通过 list() 函数将其转换为列表
doubled_numbers = list(result)
print(doubled_numbers)  # 输出: [2, 4, 6, 8, 10]
```

在上面的示例中，我们定义了一个函数 `double(x)`，它将传入的数字加倍。然后我们有一个包含数字的列表 `numbers`，我们使用 `map()` 函数将 `double()` 函数应用到列表的每个元素上，返回一个迭代器 `result`，最后使用 `list()` 函数将迭代器转换为列表 `doubled_numbers`。

`map()` 函数非常灵活，可以用于处理不同类型的数据和函数，使得对可迭代对象进行批量处理变得非常方便。

### fibo![image-20230804113656032](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804113656032.png)

### filter

返回的也是新的list



![image-20230804113737648](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804113737648.png)

### eval()



可以用于字符串表示的值，并且将这个值返回

就像是x*y，如果不用这个函数，那就是一个简单的字符串，但是eval能够将这个字符串当成代码执行，所以sum的值才是200

**同样这样的方法也有风险**就在下面的那个可能创造回污染变量空间的变量

![image-20230811164330812](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230811164330812.png)

![image-20230811164335582](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230811164335582.png)

**还有一个exec*

**与eval不同的是，这个exec不会返回值，它本身那就是一条语句**

![image-20230816190638695](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816190638695.png)

![image-20230816190848313](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816190848313.png)

![image-20230816190942318](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816190942318.png)**给exec添加这样的参数就可以防止午饭，scope**





### zip

![image-20230816173052323](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816173052323.png)

缝合两个列表运用于并行迭代

### sorted

这个不是列表中的sort函数，他回返回一个按照要求排序好的可以迭代对象

### reversed

与上面同理，返回的是一个反转好的迭代器

# 文件

**打开文件**

![image-20230804201405348](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804201405348.png)

open的默认mode是''r''

![image-20230804204504747](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804204504747.png)

当解析码不一样的时候得指定具体的encoding



**以二进制打开文件**

![image-20230804204613807](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804204613807.png)

![image-20230804204917141](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230804204917141.png)

 

二进制写入如果再添加文本的话，还是会报错

文件的修改，需要拖入内存修改，然后清空源文件，然后再把内容写回硬盘

![image-20230806190439145](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230806190439145.png)

# 常用模块和模块的介绍

## 模块的分类

- 标准模块

- 内置模块

- 库（上述300）

- 第三方模块

  

## 模块的导入

![image-20230818174551983](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818174551983.png)同时导入两个模块，加逗号

![image-20230818174645845](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818174645845.png)

引用rename这个方法的时候不需要'.'

![image-20230818174816054](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818174816054.png)

**甚至可以直接具体到直接的方法**

![image-20230818175028448](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818175028448.png)这种导入是导入的方法，但是给他重新命名了

![image-20230818175124598](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818175124598.png)

导入全部的方法（不推荐这种导入方法）



## os

`os` 模块是Python标准库中的一个模块，提供了与操作系统交互的各种功能。它可以用于管理文件和目录、执行系统命令、获取环境变量等。以下是一些 `os` 模块中常用的函数和属性：

### 文件和目录操作：

- `os.getcwd()`：获取当前工作目录。
- `os.chdir(path)`：改变当前工作目录。
- `os.listdir(path)`：返回指定目录下的文件和子目录列表。
- `os.mkdir(path)`：创建一个新目录。
- `os.makedirs(path)`：递归地创建多级目录。
- `os.remove(path)`：删除指定文件。
- `os.rmdir(path)`：删除指定目录。
- `os.path.exists(path)`：检查路径是否存在。

### 路径操作：

- `os.path.join(path, *paths)`：连接多个路径组件。
- **`os.path.abspath(path)`：返回绝对路径。**
- `os.path.basename(path)`：返回路径的基本名称。
- `os.path.dirname(path)`：返回路径的目录部分。
- `os.path.isfile(path)`：检查路径是否为文件。
- `os.path.isdir(path)`：检查路径是否为目录。

### 系统环境：

- `os.environ`：一个包含环境变量的字典。
- `os.getenv(varname, default=None)`：获取指定环境变量的值。

### 执行系统命令：

- `os.system(command)`：在子shell中执行系统命令。
- `os.popen(command[, mode[, bufsize]])`：执行系统命令并返回一个文件对象。

### 其他常用功能：

- `os.name`：操作系统的名称，通常是 `'posix'` 或 `'nt'`。
- `os.pathsep`：路径分隔符，`':'`（POSIX系统）或 `';'`（Windows系统）。
- `os.linesep`：行分隔符，`'\n'`（POSIX系统）或 `'\r\n'`（Windows系统）。

这些只是 `os` 模块中的一些常用函数和属性。根据你的需要，你可以进一步探索 `os` 模块的其他功能，以便进行更多类型的操作，如文件移动、复制、重命名、执行系统调用等。



## sys

![image-20230818182956551](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818182956551.png)



`sys` 模块是Python标准库中的另一个重要模块，用于与Python解释器和操作系统交互，提供了许多与系统相关的功能。以下是一些 `sys` 模块中常用的函数和属性：

### Python解释器相关：

- `sys.argv`：命令行参数列表。可以用来获取运行Python脚本时传递的命令行参数。
- `sys.exit([arg])`：终止程序的运行，可传递一个退出码。

### 运行时环境：

- `sys.version`：Python解释器的版本信息。
- `sys.platform`：运行Python的平台信息。
- `sys.path`：Python搜索模块的路径列表。
- `sys.modules`：已导入的模块字典。

### 标准输入输出：

- `sys.stdin`：标准输入流。
- `sys.stdout`：标准输出流。
- `sys.stderr`：标准错误流。

### 递归限制：

- `sys.getrecursionlimit()`：获取递归深度的限制。
- `sys.setrecursionlimit(limit)`：设置递归深度的限制。

### 内存管理：

- `sys.getsizeof(object[, default])`：返回对象的内存大小。
- `sys.getrefcount(object)`：返回对象的引用计数。

### 其他常用功能：

- `sys.maxsize`：最大的整数。
- `sys.exc_info()`：获取当前异常信息。
- `sys.getdefaultencoding()`：获取默认字符串编码。
- `sys.settrace(func)`：设置全局的跟踪函数。

这些只是 `sys` 模块中的一些常用函数和属性。通过使用这些函数和属性，你可以获得关于运行时环境、命令行参数、标准输入输出等信息，并进行一些系统级别的操作。根据需要，你可以进一步探索 `sys` 模块的其他功能，以便更好地理解和控制Python程序的运行。

## time和datatime

### 时间戳

时间戳（Timestamp）是一个表示时间的数字，通常以某个固定的基准时间（通常是格林尼治标准时间，也称为UTC）为起点，以秒为单位进行计数。时间戳可以用来记录某个事件发生的具体时间，计算时间间隔，或进行时间相关的计算。

在计算机中，时间戳通常用整数或浮点数来表示，整数部分表示秒数，浮点数部分表示小数秒。在Python中，`time` 模块的 `time()` 函数可以获取当前的时间戳，返回一个浮点数。

时间戳在很多应用中都是非常有用的，比如：

- 记录事件发生的时间，用于日志记录、数据分析等。
- 进行时间间隔的计算，比如计算程序运行时间、操作的时长等。
- 在网络通信中，时间戳可以用来同步不同设备的时钟。
- 数据库中的时间戳字段可以用于记录数据的创建或修改时间。

示例：

```python
import time

# 获取当前时间戳
timestamp = time.time()
print("Current Timestamp:", timestamp)

# 使用时间戳进行时间间隔计算
start_time = time.time()
time.sleep(2)  # 等待2秒
end_time = time.time()
elapsed_time = end_time - start_time
print("Elapsed Time:", elapsed_time, "seconds")
```

需要注意的是，时间戳通常是与特定的基准时间相关联的，因此在不同的上下文中可能会有不同的基准时间。在Python中，时间戳的计算通常以1970年1月1日UTC为基准时间，称为UNIX时间戳。不同编程语言和系统可能采用不同的基准时间，因此在跨平台或跨语言应用中需要格外注意。

### time中常用的方法

`time` 模块是Python标准库中的一个模块，用于处理时间相关的操作。它提供了许多函数和类，用于获取当前时间、处理时间戳、计时等。以下是一些 `time` 模块中常用的函数和属性：

获取时间：

- `time.time()`：返回当前时间的时间戳，以秒为单位。

- `time.localtime([secs])`：将一个时间戳转换为本地时间的结构化对象。

- `time.gmtime([secs])`：将一个时间戳转换为UTC（协调世界时）的结构化对象。

- `time.ctime([secs])`：将一个时间戳转换为可读的时间字符串。

- `time.strftime(format[, t])`：将一个时间结构化对象转换为格式化的字符串。

  ![image-20230818194838803](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818194838803.png)

  可以输出指定的参数

时间戳和结构化时间之间的转换：

- `time.mktime(t)`：将一个结构化时间转换为时间戳。
- `time.strptime(string, format)`：将一个格式化的时间字符串解析为结构化时间。

计时和延时：

- `time.sleep(secs)`：在当前线程睡眠指定的秒数。

其他常用功能：

- `time.clock()`（在Python 3.3 之前）：返回当前的CPU时间（包括睡眠时间）。在Python 3.3+ 中已被废弃，推荐使用 `time.process_time()`。
- `time.process_time()`：返回当前的CPU时间（不包括睡眠时间）。

示例：

```python
import time

# 获取当前时间戳
timestamp = time.time()
print("Timestamp:", timestamp)

# 将时间戳转换为本地时间的结构化对象
local_time = time.localtime(timestamp)
print("Local Time:", local_time)

# 将结构化时间转换为格式化字符串
formatted_time = time.strftime("%Y-%m-%d %H:%M:%S", local_time)
print("Formatted Time:", formatted_time)

# 等待一段时间
print("Waiting for 2 seconds...")
time.sleep(2)
print("Done waiting!")
```

`time` 模块提供了处理时间的基本功能，如果需要更高级的时间操作（例如涉及时区、日期计算等），可能需要使用 `datetime` 模块。

### datatime

### datetime.timedelta(日期间的运算)

后面的参数符号可以是±，用于代表增加或减少

![image-20230818200547558](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818200547558.png)

t1现在的时间

`datetime` 模块是Python标准库中用于处理日期和时间的模块，提供了许多功能以便于创建、操作和格式化日期时间数据。它在处理时间的各种操作上比 `time` 模块更为高级和灵活。

以下是一些 `datetime` 模块中常用的类和函数：

#### datetime 类：

`datetime` 类用于表示一个完整的日期和时间，包括年、月、日、时、分、秒以及微秒。可以使用 `datetime(year, month, day, hour, minute, second, microsecond)` 构造函数来创建一个 `datetime` 对象。

```python
import datetime

now = datetime.datetime.now()
print("Current DateTime:", now)
```

#### `date` 类：

`date` 类用于表示一个日期（年、月、日），没有时间信息。可以使用 `date(year, month, day)` 构造函数来创建一个 `date` 对象。

```python
import datetime

today = datetime.date.today()
print("Today's Date:", today)
```



## random

![image-20230818201801321](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818201801321.png)

![image-20230818202228075](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230818202228075.png)random.choie的数据源可以结合str的数字或者字母，生成随机验证码

还有一个比较重要的就是random.shuffle()这个方法，十分的香，随机打乱，数据源必须是**列表**，返回的不是新列表，是在原列表的基础上

## 序列化pickle

字典变成字符串--序列化

 ![image-20230819175910610](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819175910610.png)

序列化是把对应的字典转换为序列化文件（十六进制byte模式）

![image-20230819180045807](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819180045807.png)

dump是直接序列化+write

![image-20230819180330943](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819180330943.png)

## json(所有语言都通用)

只能dump或者load一次，这是与pickle的主要区别

![image-20230819180857088](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819180857088.png)



## hashlib

**MD5**

同一值的md5加密值是一样的

密文无法反推出明文

![image-20230819182918815](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819182918815.png)

```python
import hashlib
m=hashlib.md5()
m.update("谢隆杰是大帅哥".encode("utf-8"))
print(m.hexdigest())


#当一行一行解释这段代码时：

#import hashlib：导入Python标准库中的 hashlib 模块，该模块提供了各种哈希函数。

#m = hashlib.md5()：创建一个 md5 哈希对象，用于计算数据的 MD5 哈希值。md5 是其中的一种哈希函数。

#m.update("谢隆杰是大帅哥".encode("utf-8"))：调用 md5 哈希对象的 update() 方法，传递字符串 "谢隆杰是大帅哥" 的 UTF-8 编码字节序列作为输入。update() 方法将该输入添加到哈希对象的内部状态中。

#print(m.hexdigest())：调用 md5 哈希对象的 hexdigest() 方法，获取计算出的 MD5 哈希值的十六进制表示，并将该哈希值以字符串形式打印出来。

#综合起来，这段代码的作用是计算字符串 "谢隆杰是大帅哥" 的 MD5 哈希值，并以十六进制形式打印出来。MD5 哈希函数将输入数据映射为一个 128 位的哈希值，通常用于数据完整性验证、密码存储等场景。在这个例子中，字符串 "谢隆杰是大帅哥" 被转换为其对应的 MD5 哈希值，并以十六进制字符串的形式输出。
```

![image-20230819185605802](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819185605802.png)



## re正则表达式

![image-20230829170930360](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829170930360.png)

找到符合规则的值

在正则表达式中，前缀 `r` 表示“原始字符串”（raw string）。使用原始字符串，可以在正则表达式中更方便地处理反斜杠 `\` 字符，因为正则表达式中常常会包含许多反斜杠作为特殊字符的转义符。

正常的字符串中，反斜杠 `\` 用于转义字符，例如 `\n` 表示换行，`\t` 表示制表符等。在正则表达式中，反斜杠同样用于转义特殊字符，例如 `\b` 表示单词边界，`\d` 表示数字等。然而，当我们需要在正则表达式中表示一个普通的反斜杠字符时，就需要使用两个反斜杠 `\\` 来转义。

使用原始字符串，Python 会将字符串中的转义字符都视为普通字符，不进行转义处理。这在正则表达式中非常有用，因为正则表达式本身也使用反斜杠作为转义字符。

例如，在您提供的正则表达式 `r'\bB\w+\b'` 中，`\b` 和 `\w` 都是正则表达式的特殊字符。如果不使用原始字符串，正则表达式可能会被解释为 `\b` 和 `\w` 的转义形式，从而导致匹配不符预期。

使用原始字符串，可以简化正则表达式的编写和阅读，特别是当正则表达式中包含许多反斜杠时，例如 `\`、`\b`、`\w` 等。

总之，使用 `r` 前缀可以让您在正则表达式中更轻松地处理反斜杠，避免不必要的转义。

### 匹配规则

![image-20230819191430482](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819191430482.png)



match，如果开头没有就停止匹配

search,只找一个

![image-20230819190921223](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819190921223.png)



![image-20230819190832076](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230819190832076.png)



![image-20230829172231371](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829172231371.png)

### 分析

这个正则表达式 `r'((ab).*?){2}.*?(ab)'` 可以分为以下几个部分：

1. `((ab).*?)`：这是一个捕获组，其中 `(ab)` 表示匹配连续的字符 "ab"。而 `.*?` 则是非贪婪匹配，匹配任意数量的字符，但尽量少地匹配，直到下一个部分出现。这整个捕获组的作用是匹配连续的 "ab" 并将其捕获。

2. `{2}`：表示前面的捕获组 `(ab).*?` 需要匹配两次，也就是需要连续匹配两个 "ab"。

3. `.*?`：这部分匹配任意数量的字符，同样使用非贪婪匹配。

4. `(ab)`：最后一个 `(ab)` 表示匹配单独的 "ab"。

综合起来，整个正则表达式的含义是：

1. 匹配连续的 "ab" 两次。
2. 然后匹配任意数量的字符。
3. 最后匹配单独的 "ab"。

这个正则表达式的一个例子是匹配连续出现两次 "ab" 并且它们之间可以包含任意数量的字符，最后再匹配一个单独的 "ab"。

例如，对于字符串 `ab123abxyzab`，该正则表达式会匹配 `ab123abxyzab`，其中第一个匹配为 `ab123ab`，第二个匹配为 `xyzab`，第三个匹配为 `ab`。

### 替换功能（sub,subn）



#### sub

![image-20230829175721513](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829175721513.png)

![image-20230829175731036](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829175731036.png)

*同样可以嵌套匿名函数*

![image-20230829175808149](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829175808149.png)

*以及设置替换次数*

![image-20230829175825005](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829175825005.png)

#### split（注意是re的对象，不是函数）

![image-20230829180408421](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829180408421.png)

### 子模式与Match对象

![image-20230829180544774](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829180544774.png)

- 子模式扩展语法：
  (?P<groupname>)：为子模式命名
  (?iLmsux)：设置匹配标志，可以是几个字母的组合，每个字母含义与编译标志相同
  (?:...)：匹配但不捕获匹配到内容
  (?P=groupname)：表示在此之前的命名为groupname的子模式
  (?#...)：表示注释
  (?=…)：用于正则表达式之后，表示如果=后的内容在字符串中出现则匹配，但不返回=之后的内容
  (?!...)：用于正则表达式之后，表示如果!后的内容在字符串中不出现则匹配，但不返回!之后的内容
  (?<=…)：用于正则表达式之前，与(?=…)含义相同
  (?<!...)：用于正则表达式之前，与(?!...)含义相同

  ![image-20230829180810380](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829180810380.png)

  ![image-20230829180949287](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230829180949287.png)



## 序列解包

![image-20230816170125801](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816170125801.png)

序列解包可以直接交换变量的值，这个在c语言中想都不敢想

## fibo

```python
fibs = [0, 1] 
num = int(input('How many Fibonacci numbers do you want? ')) 
for i in range(num-2): 
 fibs.append(fibs[-2] + fibs[-1]) 
print(fibs)
```

# 包

## math

### gcd(求最大公约数)

![image-20230816204230760](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816204230760.png)

![image-20230816204236062](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230816204236062.png)

