#  Leture

## Week2

### 2.2

![image-20231101184714663](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231101184714663.png)

public method should stay forever

nested class(嵌套类)

可以随意地移动类在类与类之间

private class通常意味着这个类的一些属性不需要被使用者知道

static需要通过类名来访问，同样static和private无法访问外部类的东西



![image-20231101202155524](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231101202155524.png)

**cache**合理使用！降低时间复杂度

```java
package lec4_lists2;

/** An SLList is a list of integers, which hides the terrible truth
   * of the nakedness within. */
public class SLList {	
	private static class IntNode {
		public int item;
		public IntNode next;

		public IntNode(int i, IntNode n) {
			item = i;
			next = n;
			// System.out.println(size);
		}
	} 

	/* The first item (if it exists) is at sentinel.next. */
	private IntNode sentinel;
	private int size;

	private static void lectureQuestion() {
		SLList L = new SLList();
		IntNode n = new IntNode(5, null);
	}

	/** Creates an empty SLList. */
	public SLList() {
		sentinel = new IntNode(63, null);
		size = 0;
	}

	public SLList(int x) {
		sentinel = new IntNode(63, null);
		sentinel.next = new IntNode(x, null);
		size = 1;
	}

 	/** Adds x to the front of the list. */
 	public void addFirst(int x) {
 		sentinel.next = new IntNode(x, sentinel.next);
 		size = size + 1;
 	}

 	/** Returns the first item in the list. */
 	public int getFirst() {
 		return sentinel.next.item;
 	}

 	/** Adds x to the end of the list. */
 	public void addLast(int x) {
 		size = size + 1; 		

 		IntNode p = sentinel;

 		/* Advance p to the end of the list. */
 		while (p.next != null) {
 			p = p.next;
 		}

 		p.next = new IntNode(x, null);
 	}
 	
 	/** Returns the size of the list. */
 	public int size() {
 		return size;
 	}

	public static void main(String[] args) {
 		/* Creates a list of one integer, namely 10 */
 		SLList L = new SLList();
 		L.addLast(20);
 		System.out.println(L.size());
 	}
}
//sentinel Nodes确保了第一个首节点不会是空，避免了后续如同addlast当第一个node is empty的情况
//这样无需考虑特殊情况！！
```

#### Invariant(不变量)

![image-20231101204554729](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231101204554729.png)

invariant advantages

- ![image-20231101204650276](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231101204650276.png)



### 2.3

Double link

![image-20231102114039010](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102114039010.png)



参数化

![image-20231102115051781](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102115051781.png)

不在拘束于同一个数据类型

e.g.![image-20231102115128651](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102115128651.png)

![image-20231102115420112](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102115420112.png)



Arrays

![image-20231102115905463](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102115905463.png)

三种初始化

![image-20231102120037517](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102120037517.png)

![image-20231102120957744](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102120957744.png)

**arraycopy**

把数组b的从零开始的index复制到x的从3开始的Index复制两个

![image-20231102121343416](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102121343416.png)

**this function is faster than loop!!**



二维数组，cool!!

#### askUser()



![image-20231102224908010](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102224908010.png)

没有指定每个引用的存放大小，也可以指定

![image-20231102222936075](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231102222936075.png)

![image-20231102223129753](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102223129753.png)

## week3



### Assertion（断言）(test)

在编程中，断言（Assertion）是一种检查表达式在运行时是否为真的方式。如果表达式计算结果为假，断言会导致程序抛出错误并通常终止执行。断言用于调试目的，帮助开发者找出程序中潜在的逻辑错误。在许多编程语言中，断言可以在运行时启用或禁用，通常在发布的产品代码中禁用。

在Java中，断言的使用可以通过`assert`关键字来实现：

```java
assert expression1;
```
或者

```java
assert expression1 : expression2;
```

其中，`expression1` 应该总是产生一个布尔值。第二种形式的断言，`expression2` 是一个提供错误信息的表达式，如果`expression1` 为`false`，则该信息会被包含在抛出的`AssertionError`中。

例如：

```java
int x = 10;
assert x > 0 : "x must be positive";
```

如果`x`不大于0，那么断言会失败，抛出一个`AssertionError`并包含消息"x must be positive"。

断言通常用于以下情况：

1. 检查不可能发生的情况（例如，检查程序的某部分是否永远不会被执行）。
2. 检查程序的某个状态是否符合预期（例如，在处理数据之后验证数据的有效性）。
3. 作为开发过程中测试代码的一种方式，但通常不用于生产环境。

在Java中，默认情况下，断言是禁用的。为了启用它们，需要在程序运行时使用`-ea`或者`-enableassertions`选项。

需要注意的是，虽然断言对于调试是有用的，但它们并不应该用于替代正常的异常处理或程序逻辑中的错误检查。断言主要是作为开发和测试过程中的一个工具，用来确保代码的逻辑正确性。在生产环境中，合适的错误处理和校验通常是通过使用异常处理机制来实现的。

#### assertThat

在Java中，`assertThat` 是一个断言方法，通常用于单元测试中，以验证代码的行为是否符合预期。这个方法是JUnit 或者其他测试库（如 Hamcrest 或 AssertJ）提供的，它们允许你编写具有更好可读性的断言语句。

例如，使用JUnit的`assertThat`方法可以这样写：

```java
import static org.junit.Assert.assertThat;
import static org.hamcrest.CoreMatchers.is;

// ... 在测试方法中
assertThat(actualValue, is(expectedValue));
```

在上面的代码中，`actualValue` 是你从测试的代码中得到的值，而`expectedValue` 是你期望得到的值。`is` 是Hamcrest提供的一个匹配器（Matcher），用于检查两个值是否相等。

AssertJ 是另一个流行的断言库，它提供了一个更为流畅的API来编写测试断言。使用AssertJ，你的测试代码可能看起来像这样：

```java
import static org.assertj.core.api.Assertions.assertThat;

// ... 在测试方法中
assertThat(actualValue).isEqualTo(expectedValue);
```

在这里，`assertThat` 后面跟着的是一系列链式调用，可以构建更复杂的断言，以及更具描述性的错误消息。

这些断言方法在编写自动化测试时非常有用，因为它们可以帮助你确保你的代码在修改后仍然按照预期工作。如果一个断言失败，那么测试框架会抛出一个错误，通常这会导致构建失败，在持续集成环境中这是非常有价值的反馈。

![image-20231105210729320](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231105210729320.png)

![image-20231105210927166](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231105210927166.png)



### TTD workflow

![image-20231105220243565](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231105220243565.png)

### Arrays

compare to list

- faster get items



Naive AlistCode

![image-20231110192058985](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110192058985.png)

Array **resizing**: 当数组越界使用System.arraycope

![image-20231110193856529](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110193856529.png)

![](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110194032455.png)

resize arraylist

however this method take O(N*N)time,**when items more time takes more**

down picture is right method 

![image-20231110195444360](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110195444360.png)



An Alist should not only be efficient in time ,but also efficent in space,so initlalization use 100*4bytes is waste space

![image-20231110195830083](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110195830083.png)

size/items.length=R

R should < 0.25





**Last**,make Alist generic



![image-20231110200328193](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110200328193.png)

![image-20231110200408699](https://raw.githubusercontent.com/xiechen274/ChenCsNote/images/images/image-20231110200408699.png)

![image-20231110200517792](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231110200517792.png)

Last,Last,because we make Alist to generic,we should adjust remove method when items empty,use item =  null

