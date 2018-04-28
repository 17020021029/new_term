# Nim Game
## problem

You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.

For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.
## 解题思路
根据提示，我们可以从1开始遍历较小的整数，那些是可以的，最后得出结论，只有4及其倍数不可以赢
## 编程实现

```C++
class Solution {
public:
    bool canWinNim(int n) {
        if(n==1||n==2||n==3)
            return true;
        return n%4;
    }
};
```

# House Robber
## problem
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

Example 1:

Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
Example 2:

Input: [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
             Total amount you can rob = 2 + 9 + 1 = 12.
            
 ## 解题思路
 分情况讨论，奇数情况下，而且最终返回值要最大
 ## 编程实现

 ```C++
 class Solution {
public:
    int rob(vector<int>& nums) {
        int res=0;
        int n=nums.size();
        if(n==0)    return 0;
        if(n==1)    return nums[0];
        if(n==2)    return max(nums[0],nums[1]);
        vector<int> f(n, 0);
        f[0] = nums[0];
        f[1] = max(nums[0], nums[1]);
        for (int i = 2; i < n; ++i)
            f[i] = max(f[i-2] + nums[i], f[i-1]);
        return f[n-1];
    }
};
 ```
