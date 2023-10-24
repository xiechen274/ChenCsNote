

## Lecture部分

### lecture1

shell

windows powshell

![image-20230620064658338](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230620064658338.png)

# 黑马linux

## 路径的描述

![image-20230714132016212](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714132016212.png)



## linux命令基础

![image-20230714133329051](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714133329051.png)

### ls命令

![image-20230714133659339](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714133659339.png)

**ls -a**

可以显示隐藏内容的文件夹

ls -l

![image-20230714134932968](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714134932968.png)

*可以给出更多文件信息*

命令选项可以叠加使用

![image-20230714135105008](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714135105008.png)

ls-h

以易于阅读的形式陈列，**必须和l一起使用**

![image-20230714135319570](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714135319570.png)***单独使用ls -l***

![image-20230714135357484](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714135357484.png)***混合使用***

**总结**

![image-20230714135421977](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714135421977.png)



### cd,pwd命令

cd命令没有参数表示回到home目录

pwd![image-20230714135858031](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714135858031.png)

### 相对路径，绝对路径，特殊路径表示符

![image-20230714140050140](C:\Users\谢隆杰\Desktop\image-20230714140050140.png)

**特殊路径符**![image-20230714140454894](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714140454894.png)

### mkdir

![image-20230714141354983](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714141354983.png)

-p选项

![image-20230714141832050](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714141832050.png)



### touch cat



**touch创建文件**

![image-20230714142426058](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714142426058.png)

cat命令查看

![image-20230714142806348](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714142806348.png)



more命令查看

![image-20230714142847856](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714142847856.png)

总结

![image-20230714142924837](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230714142924837.png)



### cp,mv,rm

**cp**

![image-20230717105052861](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717105052861.png)

***复制文件夹需要带上-r的选项***

**mv**

移动文件或者文件夹

![image-20230717105336563](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717105336563.png)

  	*没有选项*

![image-20230717105708958](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717105708958.png)

如果移动到不存在的文件夹里面，就会进行改名效果

***文件夹或者文件都可以直接被移动，如果没有对应目标就是改名效果***

**rm**

![image-20230717105844605](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717105844605.png)



![image-20230717110402802](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717110402802.png)

### which，find

**which**，查找命令文件的程序文件

![image-20230717111257795](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717111257795.png)





**find**

查找指定文件

![image-20230717111441352](C:\Users\谢隆杰\Desktop\image-20230717111441352.png)

**同样find也可以使用通配符**

![image-20230717111856048](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717111856048.png)

![image-20230717111957543](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717111957543.png)

​									*查找以test结尾的文件*

![image-20230717112135597](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230717112135597.png)

### grep命令，wc命令(筛选和统计)



![image-20230718132613298](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718132613298.png)

![image-20230718132943918](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718132943918.png)

赛选过的被标红了



**wc**

![image-20230718133013474](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718133013474.png)

![image-20230718133215269](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718133215269.png)

*不加参数*

### 管道符（更改i/o流）

![image-20230718133300157](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718133300157.png)

 grep和其他命令结合相使用结合管道，**如果有多个管道符，运算顺序就是从左到右S**

![image-20230718135235648](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718135235648.png)

### echo tail 重定向符号

**echo**

![image-20230718135812015](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718135812015.png)

被反引号包围的字符串可以作为命令被执行

![image-20230718140809607](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718140809607.png)

![image-20230718140753228](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718140753228.png)

### vim编辑器



![image-20230718141901371](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718141901371.png)

有三种不同的工作模式

![image-20230718142235299](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718142235299.png)![image-20230718142336409](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718142336409.png)

![image-20230718142401809](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718142401809.png)

vim +w文件路径进入

进入之后“i”进去输入模式

输入完之后“:”进入底线命令模式+wq保存并且退出

w是保存 q是退出

vim命令模式下的快捷键

![image-20230718143035390](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718143035390.png)

![image-20230718143830184](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230718143830184.png)





### 认识root用户



![image-20230721203253248](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721203253248.png)

![image-20230721203331442](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721203331442.png)

**普通用户无法再根目录下创建文件夹**，权限一般只在home目录是不受限制的，其他地方一般是只有只读和执行权限

**切换用户命令**

![image-20230721203526233](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721203526233.png)

![image-20230721203803870](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721203803870.png)

**从root切换到其他用户的时候不需要密码，普通user切换到root需要密码**

![image-20230721203911553](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721203911553.png)

**sudo需要提前为用户配置**

为普通用户配置sudo认证
![image-20230721204115811](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721204115811.png)

### 用户，用户组管理

![image-20230721205304668](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721205304668.png)

#### 用户组

groupadd 

groupdel

![image-20230721205727344](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721205727344.png)

#### 用户（创建，删除，查看，移动）

![image-20230721205828751](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721205828751.png)

![image-20230721210034170](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721210034170.png)

![image-20230721210434810](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721210434810.png)**getnet**(查看有哪些用户)

总结

![image-20230721210650717](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721210650717.png)

### 查看权限控制

![image-20230721211121035](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721211121035.png)





![image-20230721211137336](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721211137336.png)

![image-20230721211525050](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721211525050.png)

### chmod

**注意只有文件文件夹的所属用户或者root才可以使用chmod**

![image-20230721211823700](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721211823700.png)

![image-20230721212626667](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721212626667.png)简洁写法

### chown

![image-20230721212820227](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20230721212820227.png)













# 快捷键部分

ctrl l清空 terminal

ctrl c 结束tail的持续追踪