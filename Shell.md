# 运行 Shell 的方法

## macos上的zsh

在 macOS 上，您可以通过几种方式指定要使用的 shell：

### 1. 更改默认 Shell
要更改您的默认登录 shell：

- 打开 Terminal。
- 输入 `chsh -s /bin/zsh` 或 `chsh -s /bin/bash` 来更改默认 shell 为 `zsh` 或 `bash`。
- 您可能需要输入您的密码来确认更改。
- 完成后，您需要注销并重新登录，或者重新打开 Terminal 窗口以使更改生效。

### 2. 临时切换 Shell
如果您只是想临时切换到另一个 shell，不更改默认设置：

- 打开 Terminal。
- 输入 `zsh` 或 `bash` 来启动相应的 shell。
- 这样做会在当前会话中切换 shell，但不会更改默认 shell。

### 3. 指定脚本解释器
在脚本的第一行，您可以通过 shebang（`#!`）指定解释器：

- 对于 `bash`：
  ```bash
  #!/bin/bash
  # Your script contents
  ```
- 对于 `zsh`：
  ```zsh
  #!/bin/zsh
  # Your script contents
  ```

将此行添加到脚本文件的顶部，确保脚本具有执行权限，然后您可以直接运行它，它将使用指定的 shell 执行。

### 4. 通过脚本运行指定 Shell
您还可以在任何 shell 中调用另一个 shell 来执行特定的脚本：

- 使用 `bash` 运行脚本：
  ```bash
  bash script.sh
  ```
- 使用 `zsh` 运行脚本：
  ```zsh
  zsh script.sh
  ```

确保脚本文件 `script.sh` 具有适当的执行权限（通过运行 `chmod +x script.sh` 来设置）。

选择使用哪个 shell 取决于您的个人喜好以及您在脚本或终端会话中需要使用的特定功能。

**1、作为可执行程序**

将上面的代码保存为 test.sh，并 cd 到相应目录：

```
chmod +x ./test.sh  #使脚本具有执行权限
./test.sh  #执行脚本
```

注意，一定要写成 **./test.sh**，而不是 **test.sh**，运行其它二进制的程序也一样，直接写 test.sh，linux 系统会去 PATH 里寻找有没有叫 test.sh 的，而只有 /bin, /sbin, /usr/bin，/usr/sbin 等在 PATH 里，你的当前目录通常不在 PATH 里，所以写成 test.sh 是会找不到命令的，要用 ./test.sh 告诉系统说，就在当前目录找。

**2、作为解释器参数**

这种运行方式是，直接运行解释器，其参数就是 shell 脚本的文件名，如：

```
/bin/sh test.sh
/bin/php test.php
```

这种方式运行的脚本，不需要在第一行指定解释器信息，写了也没用。

## 方法的区别

在Bash shell中，`source`命令和使用`./fileName`执行脚本的方法都可以用来运行脚本文件，但它们之间有一些关键的区别：

1. **执行环境**:
   - `source`命令（或者在某些shell中的`.`命令）会在当前shell环境中执行脚本。这意味着脚本中的所有变量和函数都会在当前shell环境中定义，对当前环境有直接影响。
   - 使用`./fileName`执行脚本会启动一个新的子shell来运行脚本。脚本执行完毕后，所有在脚本中定义的变量和函数都会随着子shell的结束而消失，不会影响当前shell环境。

2. **权限要求**:
   - `source`命令不需要脚本文件有执行权限，只需要有读权限即可。
   - 使用`./fileName`执行脚本时，脚本文件必须具有执行权限（即必须使用`chmod`命令赋予执行权限）。

3. **使用场景**:
   - 如果你想要脚本中的变量或函数在当前shell中持续有效，或者你想要修改当前shell的环境（例如改变目录或定义环境变量），你应该使用`source`命令。
   - 如果你想要在隔离的环境中运行脚本，不影响当前shell，或者你正在运行一个独立的应用程序，你应该使用`./fileName`方法。

4. **传递参数**:
   - 两种方法都允许向脚本传递参数。但是，使用`source`命令时，脚本中的退出状态（`$?`）不会覆盖当前shell的退出状态。

5. **位置独立性**:
   - `source`命令可以用于任何路径下的脚本，只要提供正确的路径。
   - 使用`./fileName`执行脚本时，`./`表示当前目录，因此你必须位于脚本所在的目录中，或者提供脚本的相对路径或绝对路径。

总结来说，`source`命令适用于当你需要在当前shell环境中保留脚本执行的结果时，而`./fileName`适用于当你需要在新的shell环境中执行脚本，不影响当前shell时。

# Shell变量

## 定义变量

定义变量时，变量名不加美元符号（$，PHP语言中变量需要），如：

your_name="runoob.com"

注意，**变量名和等号之间不能有空格**同时，变量名的命名须遵循如下规则：

- 命名只能使用英文字母，数字和下划线，首个字符不能以数字开头。
- 中间不能有空格，可以使用下划线 **_**。
- 不能使用标点符号。
- 不能使用bash里的关键字（可用help命令查看保留关键字）。

有效的 Shell 变量名示例如下：

```shell
RUNOOB
LD_LIBRARY_PATH
_var
var2
```

无效的变量命名：

```
?var=123
user*name=runoob
```

除了显式地直接赋值，还可以用语句给变量赋值，如：

```shell
your_name="qinjx"
echo $your_name
echo ${your_name}
```

以上语句将 /etc 下目录的文件名循环出来。

## 使用变量

使用一个定义过的变量，只要在变量名前面加美元符号即可，如：

```shell
your_name="qinjx"
echo $your_name
echo ${your_name}
```

花括号可以帮助shell识别变量的边界，加不加都可以

```shell
for skill in Ada Coffe Action Java; do
    echo "I am good at ${skill}Script"
done
```

**只有使用变量的时候才需要加$**

## 只读变量

使用readonly设置

```shell
#!/bin/bash

myUrl="https://www.google.com"
readonly myUrl
myUrl="https://www.runoob.com"
```

**只读变量的值不能被改变**

## 删除变量

unset命令

unset + `variable_name`

```shell
#!/bin/sh

myUrl="https://www.runoob.com"
unset myUrl
echo $myUrl
```

在echo之前unset了变量myUrl所以不会输出任何东西

## 变量类型

运行shell时，会同时存在三种变量：

- **1) 局部变量** 局部变量在脚本或命令中定义，仅在当前shell实例中有效，其他shell启动的程序不能访问局部变量。
- **2) 环境变量** 所有的程序，包括shell启动的程序，都能访问环境变量，有些程序需要环境变量来保证其正常运行。必要的时候shell脚本也可以定义环境变量。
- **3) shell变量** shell变量是由shell程序设置的特殊变量。shell变量中有一部分是环境变量，有一部分是局部变量，这些变量保证了shell的正常运行

## Shell字符串

字符串可以用单引号，也可以用双引号，也可以不用引号。

![image-20231107184206098](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231107184206098.png)

各种引号的解释

### 单引号

单引号字符串的限制：

- 单引号里的任何字符都会原样输出，单引号字符串中的变量是无效的；
- 单引号字串中不能出现单独一个的单引号（对单引号使用转义符后也不行），但可成对出现，作为字符串拼接使用。

### 双引号

```shell
your_name="runoob"
str="Hello, I know you are \"$your_name\"! \n"
echo -e $str
```

输出结果

```shell
Hello, I know you are "runoob"! 
```

- 双引号里面可以有变量
- 双引号力可以出现转义字符

### 字符串的拼接

```shell
your_name="runoob"
# 使用双引号拼接
greeting="hello, "$your_name" !"
greeting_1="hello, ${your_name} !"
echo $greeting  $greeting_1

# 使用单引号拼接
greeting_2='hello, '$your_name' !'
greeting_3='hello, ${your_name} !'
echo $greeting_2  $greeting_3
```

输出结果

```shell
hello, runoob ! hello, runoob !
hello, runoob ! hello, ${your_name} !#单引号里面没办法引用变量
```

### 获取字符串长度

`#`是获取字符串长度的符号，也可以获取数组的长度

```shell
string="abcd"
echo ${#string}   # 输出 4
```

变量为字符串时，**${#string}** 等价于 **${#string[0]}**:

```shell
string="abcd"
echo ${#string[0]}
```

### 字符串切片



length代表着包含字符的数量

在 Bash shell 中，字符串切片是一种从字符串中提取子字符串的方法。这可以通过使用一组特定的语法规则来完成。以下是一些主要的字符串切片方法：

1. **提取子字符串**:
   - 语法：`${string:position:length}`
   - `string` 是要切片的变量名。
   - `position` 是开始切片的位置（基于0的索引）。
   - `length` 是要提取的子字符串的长度。

   **案例**:
   ```bash
   str="Hello, World!"
   echo ${str:7:5}  # 输出 "World"
   ```

2. **从字符串开头提取子字符串**:
   - 语法：`${string:position}`
   - 如果省略 `length`，则从 `position` 开始提取直到字符串的末尾。

   **案例**:
   ```bash
   str="Hello, World!"
   echo ${str:7}  # 输出 "World!"
   ```

3. **从字符串末尾提取子字符串**:
   - 语法：`${string: -position:length}`
   - `position` 从字符串的末尾开始计算，必须是负数。注意 `-position` 前面的空格是可选的，但如果没有空格，前面需要加上一个冒号。

   **案例**:
   ```bash
   str="Hello, World!"
   echo ${str: -6:5}  # 输出 "World"
   ```

4. **移除字符串开头的部分**:
   - 语法：`${string#pattern}`（移除最短匹配）或 `${string##pattern}`（移除最长匹配）
   - `pattern` 是一个通配符模式，用来匹配字符串开头的部分。

   **案例**:
   ```bash
   file="example.tar.gz"
   echo ${file#*.}      # 输出 "tar.gz"，移除了第一个点之前的部分（最短匹配）
   echo ${file##*.}     # 输出 "gz"，移除了最后一个点之前的部分（最长匹配）
   ```

5. **移除字符串末尾的部分**:
   - 语法：`${string%pattern}`（移除最短匹配）或 `${string%%pattern}`（移除最长匹配）
   - 这与移除字符串开头的部分相似，但是应用于字符串的末尾。

   **案例**:
   ```bash
   file="example.tar.gz"
   echo ${file%.*}      # 输出 "example.tar"，移除了最后一个点之后的部分（最短匹配）
   echo ${file%%.*}     # 输出 "example"，移除了第一个点之后的所有部分（最长匹配）
   ```

这些是 Bash 中处理字符串切片的一些基本方法。通过组合使用这些方法，你可以灵活地处理和操作字符串数据。

# shell数组

bash目前只至此一维数组，不限定数组的大小

下标同样从0开始

## 定义数组

在 Shell 中，用括号来表示数组，数组元素用"空格"符号分割开。定义数组的一般形式为：

```shell
#数组名=(值1 值2 ... 值n)
array_name=(value0 value1 value2 value3)#注意此处的多重变量是通过空格隔开，不是逗号
#或者
array_name=(
value0
value1
value2
value3
)
#还可以单独定义数组的各个分量，与c语言类似
array_name[0]=value0
array_name[1]=value1
array_name[3]=valuen

```

## 读取数组

一般格式

```shell
#${数组名[下标]},例如
valuen=${array_name[n]}#此处使用变量依然使用美元符号$

#此外用`@`符号可以获取数组的所有元素
echo ${array_name[@]}

```

## 获取各种长度

```shell
# 取得数组元素的个数
length=${#array_name[@]}
# 或者
length=${#array_name[*]}
# 取得数组单个元素的长度
length=${#array_name[n]}
```

## 关联数组

关联数组的声明需要借助declare

```shell
declare -A my_array

```

实例

```shell
declare -A site=(["google"]="www.google.com" ["runoob"]="www.runoob.com" ["taobao"]="www.taobao.com")
#有点像是python中的字典
```

### 访问（遍历）关联数组

```shell
echo "Name: ${my_array[name]}"
echo "Age: ${my_array[age]}"
echo "Country: ${my_array[country]}"

```

输出

```shell
Name: Alice
Age: 30
Country: Wonderland

```

**遍历关联数组**

```shell
for key in "${!my_array[@]}"; do
  echo "$key: ${my_array[$key]}"
done
#这个循环将遍历所有的键，"${!my_array[@]}" 是一种特殊的语法，它返回数组中所有的键。
```

**删除键值对**

使用unset

# Shell注释

单行注释就通过"#"

## 多行注释

```shell
:<<EOF
注释内容...
注释内容...
注释内容...
EOF
```

以上例子中，**:** 是一个空命令，用于执行后面的 Here 文档，**<<'EOF'** 表示开启 Here 文档，COMMENT 是 Here 文档的标识符，在这两个标识符之间的内容都会被视为注释，不会被执行。

EOF 也可以使用其他符号:

```shell
: <<'COMMENT'
这是注释的部分。
可以有多行内容。
COMMENT

:<<'
注释内容...
注释内容...
注释内容...
'

:<<!
注释内容...
注释内容...
注释内容...
!
```

**直接使用 : 号**

我们也可以使用了冒号 **:** 命令，并用单引号 **'** 将多行内容括起来。由于冒号是一个空命令，这些内容不会被执行。

格式为：**: + 空格 + 单引号**。

```shell
: '
这是注释的部分。
可以有多行内容。
'
```



# Shell的参数传递

![image-20231111131712870](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231111131712870.png)

脚本内获取参数的格式为：**$n**。**n** 代表一个数字，$0代表的是脚本路径

实例

```shell
#!/bin/bash

echo "Shell 传递参数实例！";
echo "执行的文件名：$0";
echo "第一个参数为：$1";
echo "第二个参数为：$2";
echo "第三个参数为：$3";
```

执行脚本

```shell
$ chmod +x test.sh 
$ ./test.sh 1 2 3
Shell 传递参数实例！
执行的文件名：./test.sh
第一个参数为：1
第二个参数为：2
第三个参数为：3

```

另外，还有几个特殊字符用来处理参数：

| 参数处理 | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| $#       | 传递到脚本的参数个数                                         |
| $*       | 以一个单字符串显示所有向脚本传递的参数。 如"$*"用「"」括起来的情况、以"$1 $2 … $n"的形式输出所有参数。 |
| $$       | 脚本运行的当前进程ID号                                       |
| $!       | 后台运行的最后一个进程的ID号                                 |
| $@       | 与$*相同，但是使用时加引号，并在引号中返回每个参数。 如"$@"用「"」括起来的情况、以"$1" "$2" … "$n" 的形式输出所有参数。 |
| $-       | 显示Shell使用的当前选项，与[set命令](https://www.runoob.com/linux/linux-comm-set.html)功能相同。 |
| $?       | 显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误。 |

$* 与 $@ 区别：

- 相同点：都是引用所有参数。
- 不同点：只有在双引号中体现出来。假设在脚本运行时写了三个参数 1、2、3，则 " * " 等价于 "1 2 3"（传递了一个参数），而 "@" 等价于 "1" "2" "3"（传递了三个参数）。

# Shell运算符

[参考链接](https://www.runoob.com/linux/linux-shell-basic-operators.html)