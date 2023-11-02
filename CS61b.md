# Leture

## Week2

### 2.2

![image-20231101184714663](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231101184714663.png)

public method should stay forever

nested class(嵌套类)

可以随意地移动类在类与类之间

private class通常意味着这个类的一些属性不需要被使用者知道

static需要通过类名来访问，同样static和private无法访问外部类的东西



![image-20231101202155524](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231101202155524.png)

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

![image-20231101204554729](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231101204554729.png)

invariant advantages

- ![image-20231101204650276](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231101204650276.png)



### 2.3

Double link

![image-20231102114039010](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102114039010.png)



参数化

![image-20231102115051781](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102115051781.png)

不在拘束于同一个数据类型

e.g.![image-20231102115128651](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102115128651.png)

![image-20231102115420112](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102115420112.png)



Arrays

![image-20231102115905463](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102115905463.png)

三种初始化

![image-20231102120037517](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102120037517.png)

![image-20231102120957744](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102120957744.png)

**arraycopy**

把数组b的从零开始的index复制到x的从3开始的Index复制两个

![image-20231102121343416](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102121343416.png)

**this function is faster than loop!!**



二维数组，cool!!

### askUser()



![image-20231102224908010](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102224908010.png)

没有指定每个引用的存放大小，也可以指定

![image-20231102222936075](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102222936075.png)

![image-20231102223129753](C:\Users\谢隆杰\AppData\Roaming\Typora\typora-user-images\image-20231102223129753.png)

