## problem
Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in-place.

Example 1:

Input: 
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
Output: 
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]

Example 2:

Input: 
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
Output: 
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
## 解题思路
开始的想法就是遍历数组后，标记第一行第一列的元素为0,然后再遍历数组，将第一行和第一列为0的元素改为0</br>
第一次实现的过程中，因为正序遍历改变了当前的值，导致其余多项改为0，应该改为倒序
## 代码实现
```C++
class Solution
{  
  public:
     void setZeroes(vector<vector<int> > &matrix)
      {
          int col0 = 1;   
          for(int i = 0; i < matrix.size(); ++ i)
          {
             if(matrix[i][0] == 0)
                 col0 = 0;
             for(int j = 1; j < matrix[i].size(); ++ j)
                 if(matrix[i][j] == 0)
                     matrix[i][0] = matrix[0][j] = 0;
         }
         for(int i = matrix.size() - 1; i >= 0; -- i)
         {
             for(int j = 1; j < matrix[i].size(); ++ j)
                 if(matrix[i][0] == 0 || matrix[0][j] == 0)
                     matrix[i][j] = 0;
             if(col0 == 0)
                 matrix[i][0] = 0;
         }
     }
 };
```
