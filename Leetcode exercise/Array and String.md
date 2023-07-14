## Q 1

https://leetcode.cn/leetbook/read/array-and-string/yf47s/
给你一个整数数组 nums ，请计算数组的 中心下标 。

数组 中心下标 是数组的一个下标，其左侧所有元素相加的和等于右侧所有元素相加的和。

如果中心下标位于数组最左端，那么左侧数之和视为 0 ，因为在下标的左侧不存在元素。这一点对于中心下标位于数组最右端同样适用。

如果数组有多个中心下标，应该返回 最靠近左边 的那一个。如果数组不存在中心下标，返回 -1 。

示例 1：

输入：nums = [1, 7, 3, 6, 5, 6]
输出：3
解释：
中心下标是 3 。
左侧数之和 sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11 ，
右侧数之和 sum = nums[4] + nums[5] = 5 + 6 = 11 ，二者相等。
示例 2：

输入：nums = [1, 2, 3]
输出：-1
解释：
数组中不存在满足此条件的中心下标。
示例 3：

输入：nums = [2, 1, -1]
输出：0
解释：
中心下标是 0 。
左侧数之和 sum = 0 ，（下标 0 左侧不存在元素），
右侧数之和 sum = nums[1] + nums[2] = 1 + -1 = 0 。

```c++
class Solution {

public:
    int pivotIndex(vector<int>& nums) {
		// 如果数组为空，直接返回 -1
		if(nums.empty()) return -1;
		//初始化左数组和 和 右数组和
		int sum_left = 0;
		int sum_right = 0;
		for(int i = 1; i < nums.size(); i++) sum_right += nums[i];
		//如果数组和相等，则返回下标，否则左加右减
		for(int i = 0; i < nums.size(); i++)
		{
			if(sum_left == sum_right) return i;
			sum_left += nums[i];
			if(i<nums.size()) sum_right -= nums[i+1];
		}
		return -1;
    }
};
```

左边和 = 右边和 可 替换为 左边和\*2 = 数组和-当前数
右边减去下一位数组时，注意考虑越界情况

## Q2
https://leetcode.cn/leetbook/read/array-and-string/cxqdh/
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为 O(log n) 的算法。

示例 1:

输入: nums = [1,3,5,6], target = 5
输出: 2
示例 2:

输入: nums = [1,3,5,6], target = 2
输出: 1
示例 3:

输入: nums = [1,3,5,6], target = 7
输出: 4

```c++
class Solution {

public:
    int searchInsert(vector<int>& nums, int target) {
		if(target < nums[0]) return -1;
		int low = 0;
		int high = nums.size()-1;
		int mid = 0;
		while(low <= high)
		{
			mid = (low + high) / 2;
			if(nums[mid] == target) return mid;
			else if(nums[mid] > target) high = mid -1;
			else if(nums[mid] < target) low = mid + 1;
		}
		return low;
    }
};
```
考虑首位极端情况，二分查找，暴力枚举
`vector.size()`得到是长度，最后一位下标应减1、

## Q3
https://leetcode.cn/leetbook/read/array-and-string/c5tv3/
合并区间
以数组 intervals 表示若干个区间的集合，其中单个区间为 intervals[i] = [starti, endi] 。请你合并所有重叠的区间，并返回 一个不重叠的区间数组，该数组需恰好覆盖输入中的所有区间 。

 

示例 1：

输入：intervals =\[[1,3],[2,6],[8,10],[15,18]]
输出：\[[1,6],[8,10],[15,18]]
解释：区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].
示例 2：

输入：intervals = \[[1,4],[4,5]]
输出：\[[1,5]]
解释：区间 [1,4] 和 [4,5] 可被视为重叠区间。

```c++
class Solution {

public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
		sort(intervals.begin(), intervals.end());
		vector<vector<int>> v;
		v.push_back(intervals[0]);
		int i = 0;
		for(int j = i+1 ; j < intervals.size(); j++)
		{
			if(v[i][1] > intervals[j][0])
			{
				v[i][1] = max(v[i][1], intervals[j][1]);
			}
			else
			{
				v.push_back(intervals[j]);
				i++;
			}
		}
		return v;
    }
};
```