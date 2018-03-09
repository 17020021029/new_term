# Rotate Image
## Problem
You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Note:
You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation. 
## 问题分析
要求90度反转，那么，一次可以转换4个数字（即正方形的四个角），如图
````
1*  2  3*               7  2  1             7  4  1

4  5  6      -->        4  5  6　　  -->   8  5  2　　

7*  8  9*               9  8  3　　　　　   9  6  3
````
## 代码实现
```ruby
void rotate(int** matrix, int matrixRowSize, int *matrixColSizes) {
    for(int i=0;i<matrixRowSize/2;i++)  //只需要从上边反转一半，即能完成反转，且只需要从j=i开始，遍历到matrirowsoze-1-i
    {
        for(int j=i;j<matrixRowSize-1-i;j++)  
        {
            int temp=matrix[i][j];
            matrix[i][j]=matrix[matrixRowSize-1-j][i];
            matrix[matrixRowSize-1-j][i]=matrix[matrixRowSize-1-i][matrixRowSize-1-j];
            matrix[matrixRowSize-1-i][matrixRowSize-1-j]=matrix[j][matrixRowSize-1-i];
            matrix[j][matrixRowSize-1-i]=temp;    //注意反转时下标变化的规律
        }
    }
}
```
## 其他解法
先按两条对角线反转，然后再按中间线上下反转（感觉这样不容易弄错下标）
```ruby
void rotate(int** matrix, int matrixRowSize, int *matrixColSizes) {
    for(int i=0;i<matrixRowSize-1;i++)  //只能读取到n-2,因为n-1是对角线
        for(int j=0;j<matrixRowSize-1-i;j++){
            int tmp;
            tmp=matrix[i][j];
            matrix[i][j]=matrix[matrixRowSize-1-j][matrixRowSize-1-i];
            matrix[matrixRowSize-1-j][matrixRowSize-1-i]=tmp;
        }
    for(int i=0;i<matrixRowSize/2;i++)
        for(int j=0;j<matrixRowSize;j++)
        {
            int tmp;
            tmp=matrix[i][j];
            matrix[i][j]=matrix[matrixRowSize-1-i][j];
            matrix[matrixRowSize-1-i][j]=tmp;
        }
}
```
