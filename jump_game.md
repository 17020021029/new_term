# Jump Game
## problem 
 Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:
A = [2,3,1,1,4], return true.

A = [3,2,1,0,4], return false. 
## 问题分析
题意是把数组元素当作跳跃的步数，看最终是否能调到最后一个元素。注意跳跃后的索引一定不能大于数组元素个数。当前索引加上此时元素大小即为下一步的数组索引。
## 代码实现
```c++
bool canJump(int* nums, int numsSize) {
    int max_position = 0;   //代表当前位置的索引
    for (int i = 0; i < numsSize && numsSize > max_position; ++i) {
        if (i > max_position) return false;
        if (i + nums[i] > max_position) 
            max_position = i + nums[i]; //不断更改当前位置
    }
    return true;//一直到循环结束都没有返回值，说明成立，即返回true
}
```
