# 289.Game of Life
## Problem
According to the Wikipedia's article: "The Game of Life, also known simply as Life, is a cellular automaton devised by the British mathematician John Horton Conway in 1970."
Given a board with m by n cells, each cell has an initial state live (1) or dead (0). Each cell interacts with its eight neighbors (horizontal, vertical, diagonal) using the following four rules (taken from the above Wikipedia article):
1.	Any live cell with fewer than two live neighbors dies, as if caused by under-population.
2.	Any live cell with two or three live neighbors lives on to the next generation.
3.	Any live cell with more than three live neighbors dies, as if by over-population..
4.	Any dead cell with exactly three live neighbors becomes a live cell, as if by reproduction.
Write a function to compute the next state (after one update) of the board given its current state.
Follow up: 
1.	Could you solve it in-place? Remember that the board needs to be updated at the same time: You cannot update some cells first and then use their updated values to update other cells.
2.	In this question, we represent the board using a 2D array. In principle, the board is infinite, which would cause problems when the active area encroaches the border of the array. How would you address these problems?
## 解题思路
题目是要求是让我们一直刷新数组，大概直到全部为0无法产生活细胞时返回？更新数组时，要注意不能直接更新，先按某一规则蒋数组进行处理，再一次遍历更新出新数组，这里可以将存活的加10，更新时除10，这样得到的就一定是1，而其他情况都得到0
## 代码实现
```C++
class Solution {
public:
    void gameOfLife(vector<vector<int>>& board) {
        
        //标记数组
        for(int i=0;i<board.size();i++){
            for(int j=0;j<board[i].size();j++){
                int count=count_neighbors(board,i,j);
                if(count==3||(count==2&&board[i][j]==1))
                    board[i][j]+=10;
            }
        }
        
        //更新数组
        for(int i=0;i<board.size();i++){
            for(int j=0;j<board[i].size();j++){
                board[i][j]=board[i][j]/10;
            }
        }
    }
    
    int count_neighbors(vector<vector<int>>& board,int i,int j){
        int count=0;
        for(int r= max (i-1,0);r <= min(i+1,(int)board.size()-1);r++){
            for(int c=max(j-1,0);c <= min(j+1,(int)board[r].size()-1);c++){//解决边界问题,一定要将board[0].size()-1转成整型
                if(r!=i||c!=j)  //？
                    count+=board[r][c]%10;
            }
        }
    return count;
    }
};
```
## 总结
核心在于判断是死失活然后进行更新，注意在计算周围活细胞数目时，边界情况的处理
