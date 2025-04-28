# 基础算法



## 快速排序  

​      	  

​	https://www.dotcpp.com/oj/problem1716.html'    

```cpp
#include<iostream> // 包含输入输出流库
#include<cstdio> // 包含C标准输入输出库
using namespace std; // 使用标准命名空间

const int n = 10000000; // 定义常量 n，表示数组的最大长度

void quick_sort(int q[], int l, int r) { // 定义快速排序函数
    if (l >= r) return; // 若左指针大于等于右指针，返回
    int x = q[l], i = l - 1, j = r + 1; // 定义基准值及左右指针
    while (i < j) { // 循环直到左右指针相遇
        do i++; while (q[i] < x); // 左指针右移直到找到大于等于基准值的元素
        do j--; while (q[j] > x); // 右指针左移直到找到小于等于基准值的元素
        if (i < j) swap(q[i], q[j]); // 若左指针小于右指针，交换两元素
    }
    quick_sort(q, l, j); // 递归处理左半部分
    quick_sort(q, j + 1, r); // 递归处理右半部分
}

int main() { // 主函数入口
    int n; // 声明变量 n，表示数组长度
    scanf("%d", &n); // 输入数组长度
    int q[n]; // 声明数组并指定大小为 n
    int l = 0, r = n - 1; // 定义数组的左右边界
    for (int i = 0; i < n; i++) scanf("%d", &q[i]); // 循环读入数组元素
    
    quick_sort(q, l, r); // 调用快速排序函数
    
    for (int i = 0; i < n; i++) cout << q[i] << " "; // 循环输出排序后的数组元素并以空格分隔
    return 0; // 返回主函数的结束状态
}

```
