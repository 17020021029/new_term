# Single Number III
## Problem
 Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

For example:

Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].

Note:

    The order of the result is not important. So in the above example, [5, 3] is also correct.
    Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?
## 代码实现
编译错误
```
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
void quickSort(int* nums,int first,int end){  
    int temp,l,r;  
    if(first>=end)return;  
    temp=nums[first];  
    l=first;r=end;  
    while(l<r){  
        while(l<r && nums[r]>=temp)
            r--;  
        if(l<r)
            nums[l]=nums[r];  
        while(l<r && nums[l]<=temp)
            l++;  
        if(l<r)
            nums[r]=nums[l];  
    }  
    nums[l]=temp;  
    quickSort(nums,first,l-1);  
    quickSort(nums,l+1,end);  
}  
int* singleNumber(int* nums, int numsSize, int* returnSize) {
    qucikSort(nums,0,numsSize-1);
    int *result=(int*)malloc(sizeof(int)*2);
    int count=0;
    for(int i=0;i<numsSize;i++)
    {
        if(nums[i]!=nums[i+1]&&(!i-1))
        {
            result[count]=nums[i];
            count++;
        }
        if(nums[i]!=nums[i-1]&&(!i+1))
        {
            result[count]=nums[i];
            count++;
        }
        if(nums[i]!=nums[i+1]&&nums[i]!=nums[i-1])
        {
            result[count]=nums[i];
            count++;
        }
    }
    return result;
}
```


## 参考代码
```ruby
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* singleNumber(int* nums, int numsSize, int* returnSize) {
    if (!nums||(numsSize < 2)) return NULL;
    int* ret=(int*)malloc(sizeof(int)*2);
    if (ret) {
        int i,x=0,y=0,flag,temp;
        for (i=0;i<numsSize;i++) 
            x^=nums[i];
        flag = x & -x; 
        for (i = 0; i < numsSize; i++) 
            if ((temp=nums[i]) & flag) y^=temp;
        ret[0] = x^y;
        ret[1] = y;
        if (returnSize) *returnSize=2;
    }
    return ret;
}
```
这个解法用到与运算，异或运算等,较为巧妙
