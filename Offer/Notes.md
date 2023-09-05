## 3 数组中的重复数字

首先判断

- 数组是否为空，数组长度是否小于等于0

- 最小值和最大值是否越界



1. 排序并查找 $O(nlong_n)$
2. 使用哈希表 $O(n)$
3. 交换查找，将`numbers[i]`和`numbers[numbers[i]]`进行对比 $O(1)$
4. 如不能更改数组，建立新数组，按下标排序进入
5. 如不能更改数组，对数字进行二分，统计每个区间所有数字出现次数是否超过区间长度



## 4 二维数组的查找

首先判断

- 矩阵是否非空，行大于0，列大于0

对于排序好（左到右递增，上到下递增）的二维数组，从右上角的数字开始对比

如果大于目标则剔除整列，如果小则剔除整行



## 5 替换空格

首先判断

- 字符串非空，长度大于0

新建字符串，or更改原字符串，会影响字符串后面的内存

便利一遍统计空格数量，增加足够长度的空余

使用双指针，p1指向原字符串结尾，p2指向新字符串结尾，逐一复制，遇空格则替换

***替换，合并字符串或数组，从后向前更节省时间复杂度***



## 6 打印链表

首先判断

- 链表头指针非空

从尾到头打印链表

1. 反转链表
2. 入栈出栈
3. 类比使用栈，可以使用递归，先打印后者再打印自身



## 7 重建二叉树

首先判断

- 前序，中序数组非空，树长大于0

前序遍历第一数字是根节点

中序遍历，遇到根节点之前都是左子树，后面为右子树

使用迭代实现

## 8 二叉树下一个节点

首先判断

- 树非空



## 9 用两个栈实现队列

从stack1中pop再push到stack2实现顺序翻转



## 10 斐波那契数列

考虑特殊值 i=0, i=1

递归+循环

类比题目：青蛙跳台阶，矩形覆盖多少种解法



## 查找&排序

查找：顺序，二分，哈希表，二叉排序树

排序：插入，冒泡，归并，快排



## 11 旋转数组的最小数字

[1 2 3 4 5] -> [3 4 5 1 2]

旋转后可视为两个排序数组，所以使用二分查找

首先判断

- 数组非空，长度大于0

设置三个位置：`index1 = 0, index2 = length - 1, indexMid = (index1 + index2) / 2`

特殊位置，`index1` 和`index2`相邻，即`index2 - index1 == 0`

[1 0 1 1 1] -> [1 1 1 0 1]

如果`index1 = index2 = indexMid`此时只能使用顺序查找



## 12 矩阵中的路径

不会啊 回溯



## 13 机器人的运动范围

回溯



## 14 剪绳子

长度为n的绳子建成m段，使乘积最大

$f(n)$为把长度n的绳子剪后乘积最大值的函数，$f(n)=max(f(i)*f(n-i))$，递归公式，从小到大，存储结果以节省时间

尽可能减长度为3的绳子，如果最后剩4, 2\*2 > 3\*1

边界值测试 0 1 2 3 4，初始长度大于5



| 与 &   | 0&0=0  | 1&0=0  | 0&1=0  | 1&1=1  |
| ------ | ------ | ------ | ------ | ------ |
| 或 \|  | 0\|0=0 | 1\|0=1 | 0\|1=1 | 1\|1=1 |
| 异或 ^ | 0^0=0  | 1^0=1  | 0^1=1  | 1^1=0  |



## 15 二进制中1的个数

- 和1做位与运算，结果为1则该位是1，然后右移

- 传统循环遍历

1100 - 1 = 1011

1100 & 1011 = 1000

- 整数减1，和原整数做与运算，会把整数最右边的1变为0

那么整数的二进制有多少1就可以操作多少次

```C++
int NumOf1(int n){
    int count = 0;
    while(n){
        count++;
        n = (n-1) & n;
    }
    return count;
}
```



## 16 数值整数次方



## 17 打印从1到最大的n位数

- n过大，考虑用字符串模拟加法运算
- n个0-9的全排列，使用递归方法，结束条件为设置数字最后一位

首先判断

- n>0

```c++
 	public static void printToMaxOfNDigits2(int n) {
        if(n <= 0) {
            return;
        }
        char[] nums = new char[n];
        recursiveProductNum(0, n, nums);
    }

    public static void recursiveProductNum(int index, int length, char[] nums) {
        if(index == length) {
            printNum(nums);
            return;
        }
        for(char i = '0'; i <= '9'; i++){
            nums[index] = i;
            recursiveProductNum(index + 1, length, nums);
        }
    }

    public static void printNum(char[] nums) {
        int index = 0;
        for(; index < nums.length; index++) {
            if(nums[index] != '0'){
                break;
            }
        }
        for(; index < nums.length; index++) {
            System.out.print(nums[index]);
        }
        System.out.println();
    }
```



## 18 删除链表的节点

- 遍历到节点，执行删除
- 复制p->next到p节点，p指向p->next->next

注意删除头结点（既是头也是尾）和尾结点



## 19 正则表达式

什么鬼哦



## 21 调整数组使奇数位于偶数前

首先判断 数组是否为空，长度是否为空

双指针，前指针找偶数，后指针找奇数，进行交换

外循环p_Begin < p_End

判断偶 `(\*p & 1) != 0`



## 22 链表倒数k结点

首先判断 头指针是否为空，k是否大于链表长度，k=0

双指针，第一个指针先行k-1步，第k步时第二个指针开始移动，当第一个指针遍历到尾指针时，第二个指针到达倒数k结点。



## 23 带环链表入口节点

首先判断 头指针是否为空，链表长度是否为空

1. 判断是否有环：快慢指针，慢指针一次一步，快指针一次两步，如果快慢相遇，则存在环
2. 计算环中结点数目：首先判断相遇节点是否为空，指针步进，同时计数，直到再次到达相遇节点
3. 找到环的入口：类似上一题，第一个指针先行移动环中节点数目，第二个指针开始移动，二者相遇时则为入口



## 24 反转链表

首先判断 链表头是否为空，链表长度是否为1（p_Next = nullptr）

需要三个指针 1. p_Node = p_Head 2. p_Next = p_Node->next 3. p_Prev = nullptr

...`A` -> `B` -> `C`...

...`A` <- `B` <- `C`...

```c++
while(pNode != nullptr){
    ListNode* pNext = pNode->m_pNext;
	if(pNext == nullptr) pReservedHead = pNode;
	pNode -> m_pNext = pPrev;
	pPrev = pNode;
	pNode = pNext
}
```



## 25 合并两个排序链表

首先判断 两个链表是否为空

**递归过程**：比较两个链表的头结点大小，较小的为新的链表头结点

```c++
ListNode* Merge(ListNode* pHead1, ListNode* pHead2){
    if(pHead1 == nullptr) return pHead2;
    else if(pHead2 == nullptr) return pHead1;
    
    ListNode* pMergeHead = nullptr;
    if(pHead1->m_value < pHead2->m_value){
        pMergeHead = pHead1;
        pMergeHead->m_pNext = Merge(pHead1->m_pNext, pHead2);
    }
     else{
        pMergeHead = pHead2;
        pMergeHead->m_pNext = Merge(pHead1, pHead2->m_pNext);
    }
    return pMergeHead;
}
```



## 26 树的子结构

Tree1是否包含Tree2

首先判断两个树是否为空

**使用递归**

1. 遍历Tree1，是否含有Tree2根节点：是，则判断根节点以下是否相同；不是，继续遍历Tree1  `HasSubTree`
2. 当Tree1含有Tree2根节点时，判断子节点是否相同 `Tree2InTree1`

```c++
bool HasSubTree(BinaryTree* pRoot1, BinaryTree* pRoot2){
    bool result = false;
    if(pRoot1 != nullptr && pRoot2 != nullptr){
        if(pRoot1->value == pRoot2->value) 
            result = Tree2InTree1(pRoot1, pRoot2);
        if(!result)
            result = HasSubTree(pRoot1->pLeft, pRoot2);
        if(!result)
            result = HasSubTree(pRoot2->pRight, pRoot2);
    }
    return result;
}

bool Tree2InTree1(BinaryTree* pRoot1, BinaryTree* pRoot2){
    if(pRoot2 == nullptr)
        return true;
    if(pRoot1 == nullptr)
        return false;
    if(pRoot1->value != pRoot2->value)
        return false;
    return Tree2InTree1(pRoot1->pLeft, pRoot2->pLeft) && Tree2InTree1(pRoot1->pRight, pRoot2->pRight);
}
```



## 27 树的镜像

首先判断树 是否为空，左右子树是否为空

1. 交换根节点左右子节点
2. 交换根右子节点的左右子节点
3. 交换根左子节点的左右子节点

**递归+遍历**

```c++
void Mirror(BinaryTrre* pRoot){
    if(pRoot == nullptr) return false;
    if(pRoot->pLeft == nullptr && pRoot->pRight == nullptr) return false;
    BinartTree* pTemp = pRoot->pLeft;
    pRoot->pLeft = pRoot->pRight;
    pRoot->pRight = pTemp;
    if(pRoot->pLeft) return Mirror(pRoot->pLeft);
    if(pRoot->pRight) return Mirror(pRoot->pRight);
}
```



## 28 对称二叉树

首先判断 树是否为空，子树是否为空

**树和树的镜像是否相同**

对比前序遍历和对称的前序遍历是否相同

Special：遍历结果相同但实际不对称，考虑空指针

```c++
bool isSymmetrical(BinaryTree* pRoot){
    return isSymmetrical(pRoot, pRoot);
}

bool isSymmetrical(BinaryTree* pRoot1, BinaryTree* pRoot2){
    if(pRoot1 == nullptr && pRoot2 == nullptr) return true;
    if(pRoot1 == nullptr || pRoot2 == nullptr) return false;
    if(pRoot1->value != pRoot2->value ) return false;
    return isSymmetrical(pRoot1->pLeft, pRoot2->pRight) && isSymmetrical(pRoot1->pRight, pRoot2->pLeft);
}
```

## 29 顺时针打印矩阵

分解问题： 打印圈，自外向内-》打印左至右，上至下，右至左，下至上

圈的起点都是（0，0）（1，1）

考虑边界情况：一行，一列，一个，多行多列

```c++
void Print(int** numbers, int rows, int columns){
    if(numbers == nullptr || rows <= 0 || columns<= 0) return;
    int start = 0;
    while(columns > start*2 && rows > start*2){
        PrintCircle(numbers, rows, columns, start);
        start++;
    }
}
```

```c++
void PrintCircle(int** numbers, int rows, int columns, int start){
    int endX = columns - start -1;
    int endY = rows - start -1;
    
    //左-》右
    for(int i=start; i<=endX; i++){
        int number = numbers[start][i];
        Print(number);
    }
    
    //上-》下
    if(start < endY)
    for(int i=start+1; i<=endY; i++){
        int number = numbers[i][endX];
        Print(number);
    }
    
    //右-》左
    if(start<endX && start< endY)
    for(int i=endX-1; i>=start; --i){
        int number = numbers[endY][i];
        Print(number);
    }
    
    //下-》上
    if(start<endX && start < endY-1)
    for(int i=endY-1; i>=start; --i){
        int number = numbers[i][start];
        Print(number);
    }
}
```

