# 4Sum II
## problem
Given four lists A, B, C, D of integer values, compute how many tuples (i, j, k, l) there are such that A[i] + B[j] + C[k] + D[l] is zero.

To make problem a bit easier, all A, B, C, D have same length of N where 0 ≤ N ≤ 500. All integers are in the range of -228 to 228 - 1 and the result is guaranteed to be at most 231 - 1.

Example:

Input:
A = [ 1, 2]
B = [-2,-1]
C = [-1, 2]
D = [ 0, 2]

Output:
2

Explanation:
The two tuples are:
1. (0, 0, 0, 1) -> A[0] + B[0] + C[0] + D[1] = 1 + (-2) + (-1) + 2 = 0
2. (1, 1, 0, 0) -> A[1] + B[1] + C[0] + D[0] = 2 + (-1) + (-1) + 0 = 0
## 解题过程
### 白痴的遍历法
#### 思路
就是找四个数组的元素，是不是能相加为0,若是，则返回值加一，然后我就想也不想直接把四层循环的写上，测试一下我是不是理解对了题
#### 编程实现
```
class Solution {
public:
    int fourSumCount(vector<int>& A, vector<int>& B, vector<int>& C, vector<int>& D) {
        int res=0;
        int len=A.size();
        for(int i=0;i<len;i++)
        {
            for(int j=0;j<len;j++)
            {
                for(int k=0;k<len;k++)
                {
                    for(int l=0;l<len;l++)
                    {
                        if(A[i]+B[j]+C[k]+D[l]==0)
                            res++;
                    }
                }
            }
        }
        return res;
    }
};
```
### 参考的代码
用了unordered_map,之前看到大家的解法也有很多用了这个，但是看了一段时间没看懂，先留着以后看</br>
感觉这个还挺专业的
[unordered_map](https://blog.csdn.net/hk2291976/article/details/51037095#11-%E7%89%B9%E6%80%A7)
```C++
class Solution {
public:
    int fourSumCount(vector<int>& A, vector<int>& B, vector<int>& C, vector<int>& D) {
        int count = 0;
        unordered_map<int, int> mp;
        for (int i = 0; i < A.size(); i++) {
            for (int j = 0; j < B.size(); j++) {
                mp[A[i]+B[j]]++;
            }
        }
        for (int i = 0; i < C.size(); i++) {
            for (int j = 0; j < D.size(); j++) {
                if (mp.find(-(C[i] + D[j])) != mp.end()) {
                    count += mp[-(C[i] + D[j])];
                }
            }
        }
        return count;
    }
};
```
分析一下代码应该是先加A和B，再与C和D的和比较，想了半天，如果不用这个的话，会很麻烦，这大概就是discuss里都用这个的原因吧
