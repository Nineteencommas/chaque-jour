# 每日OJ

## LC 719. 找出第 K 小的数对距离

> 数对 (a,b) 由整数 a 和 b 组成，其数对距离定义为 a 和 b 的绝对差值。
给你一个整数数组 nums 和一个整数 k ，数对由 nums[i] 和 nums[j] 组成且满足 0 <= i < j < nums.length 。返回 所有数对距离中 第 k 小的数对距离。

这道题可以说是故事的起点，想了好久才想明白为啥二分可以二分出正确的值。

这道题二分的是数对的距离，也就是说先对数组排序，然后可以知道数对距离在 $[0,nums的最大值-nums的最小值]$之间。  
问题转化为如何在$[0,nums的最大值-nums的最小值]$这个区间内，找到第k小的那个数，就可以用二分。有left有right有mid，
判断mid这个距离，有多少个数对是小于mid这个距离的，如果小于等于mid的结果大于k，那说明应该在左侧区间找，如果小于k，那说明应该在右侧区间找。

* 值得注意的是这个收束的条件
应该找到区间里的一个数，再往左走一步，当前的数，满足的数对距离就会小于k，正好是这个数的时候等于k了，就说明是这个数应该返回
所以代码是这样写的
```java
while(left<=right) {
    
}
return left;
```


## LC 1089 复制零
> 给你一个长度固定的整数数组 arr，请你将该数组中出现的每个零都复写一遍，并将其余的元素向右平移。
注意：请不要在超过该数组长度的位置写入元素。  

> 示例 1：
输入：[1,0,2,3,0,4,5,0]   
输出：null  
解释：调用函数后，输入的数组将被修改为：[1,0,0,2,3,0,0,4]


```java
int countZero = 0;
for (int num : arr) {
    if (num == 0) {
        countZero++;
    }
}
int old = arr.length - 1;
int newIndex = old + countZero;
while (old >= 0 && newIndex >= 0) {
    if (arr[old] == 0) {
        if (newIndex < arr.length) {
            arr[newIndex] = 0;
        }
        newIndex--;
    }
    if (newIndex < arr.length) {
        arr[newIndex] = arr[old];
    }
    newIndex--;
    old--;
}
```
简单题都写了两天，OJ虽好浪费时间也是真的浪费时间。   
双指针思路，倒序遍历解决元素覆盖写入问题。old指针指向原数组的末尾，new指针指向复制完0后的新数组的末尾，两个指针模拟--。


