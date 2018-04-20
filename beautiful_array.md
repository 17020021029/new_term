# Beautiful Array
## Problem
 Suppose you have N integers from 1 to N. We define a beautiful arrangement as an array that is constructed by these N numbers successfully if one of the following is true for the ith position (1 <= i <= N) in this array:

    The number at the ith position is divisible by i.
    i is divisible by the number at the ith position.

Now given N, how many beautiful arrangements can you construct?

Example 1:

Input: 2
Output: 2
Explanation: 

The first beautiful arrangement is [1, 2]:

Number at the 1st position (i=1) is 1, and 1 is divisible by i (i=1).

Number at the 2nd position (i=2) is 2, and 2 is divisible by i (i=2).

The second beautiful arrangement is [2, 1]:

Number at the 1st position (i=1) is 2, and 2 is divisible by i (i=1).

Number at the 2nd position (i=2) is 1, and i (i=2) is divisible by 1.

Note:

    N is a positive integer and will not exceed 15.
## 问题分析
看是否是漂亮排列的算法简单，只需要判断一下，那要遍历所有的可能的数组，就要用到杂烩哦全排列的算法，可以用递归，每次交换任意的元素
## 代码实现
```C++
class Solution {
public:
    int countArrangement(int N) {
        vector<int> num(N);
        for(int i=0;i<N;i++)
        {
            num[i]=i+1;
        }
        return findWays(num,N); 
    }
    int findWays(vector<int>& num,int idex){
        int res=0;
        if(idex<=0) return 1;
        for(int i=0;i<idex;i++)
        {
            if(num[i]%idex==0||idex%num[i]==0)
            {
                swap(num[i],num[idex-1]);
                    res+=findWays(num,idex-1);
                swap(num[i],num[idex-1]);
            }
        }
        return res;
    }
};
```
