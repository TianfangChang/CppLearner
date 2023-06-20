## 数组中的重复数字 P39

首先判断

- 数组是否为空，数组长度是否小于等于0

- 最小值和最大值是否越界



1. 排序并查找 $O(nlong_n)$
2. 使用哈希表 $O(n)$
3. 交换查找，将`numbers[i]`和`numbers[numbers[i]]`进行对比 $O(1)$
4. 如不能更改数组，建立新数组，按下标排序进入
5. 如不能更改数组，对数字进行二分，统计每个区间所有数字出现次数是否超过区间长度



## 二维数组的查找 P44

首先判断

- 矩阵是否非空，行大于0，列大于0

对于排序好（左到右递增，上到下递增）的二维数组，从右上角的数字开始对比

如果大于目标则剔除整列，如果小则剔除整行



## 替换空格

首先判断

- 字符串非空，长度大于0

新建字符串，or更改原字符串，会影响字符串后面的内存

便利一遍统计空格数量，增加足够长度的空余

使用双指针，p1指向原字符串结尾，p2指向新字符串结尾，逐一复制，遇空格则替换

***替换，合并字符串或数组，从后向前更节省时间复杂度***