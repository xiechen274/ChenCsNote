# 树

## 基本知识

根节点的下方是子节点

![image-20231114110129427](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114110129427.png)

B是A节点的子节点

BCD是兄弟节点

A是B的父节点

E下面没有节点了，就成为叶子节点，CD也是叶子节点

**深度**：一个节点的深度是从根节点到自己的边的数量，E的深度就是2

**高度**：节点的高度就是从**最深**的节点到自己边的数量，A的高度是2

### 二叉树（binary tree）

二叉树是一种特殊的树，二叉树每个节点最多只有两个子节点

![image-20231114110524586](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114110524586.png)

b树，**满二叉树**，每个检点都有两个子节点

C树，完全二叉树

![image-20231114110826201](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114110826201.png)

### 顺序存储

![image-20231114111038657](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114111038657.png)

1是根节点的索引

i是父节点所在的索引 

左子树：i*2

右子树：i *2+1

![image-20231114111336692](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114111336692.png)

同样可以做除法就可以得到父节点的父节点索引

## 树的遍历

![image-20231114111945474](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114111945474.png)



- 前序遍历

  **当前节点**-左子树-右子树（a,b,d,h,e,c,f,g）

- 中序遍历

  左子树——**当前节点**——右子树

  ![image-20231114112325563](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114112325563.png)

- 后序遍历

  左子树---右子树---**当前节点**

  ![image-20231114112344249](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114112344249.png)

     *`上方不完整`*

  ADT实现树的构造

![image-20231114120301069](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114120301069.png)

**前序遍历**

![image-20231114120405888](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114120405888.png)

**中序遍历**

![image-20231114120434124](D:%5CCsNote%5Cimage-20231114120434124.png)

**后续遍历**

![image-20231114120459641](D:%5CCsNote%5Cimage-20231114120459641.png)

## 二叉搜索树

![image-20231114230436264](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231114230436264.png)

**二叉搜索树的实现**



**二叉搜索树的删除**

1.叶子节点，直接把对应的父节点指针设为null

2.只有一个子节点，叶子节点，八对应的父节点指向的指针设置为该节点的子节点

**3.有两个节点**，从右子树中找到最小数，将需要删除的结点的值，置换为该值，并且删除右子树中，最小的节点





## lab

实验6  二叉树操作
一、	实验目的
掌握二叉树的基本概念，二叉树的存储结构使用链表。
二、	实验内容
1、	

输入一个完全二叉树的层次遍历字符串，创建这个二叉树，输出这个二叉树的前序遍历字符串、中序遍历字符串、后序遍历字符串、结点数目、二叉树高度(上述每一个结果独立一行显示)。

2、	

输入二叉树前序序列和中序序列(各元素各不相同)，创建这个二叉树，输出该二叉树的后序序列、层次遍历。
三、	测试用例及答案
测试如下所有测试用例，确保输出结果的格式完全一样。