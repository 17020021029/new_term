# word search
## problem
 Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

For example,
Given board =
````
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]
````
word = "ABCCED", -> returns true,
word = "SEE", -> returns true,
word = "ABCB", -> returns false.
## 问题分析
给定一个二维数组和一个字符串，看自否串是否可以在数组中连续找到。
## 代码实现
```C++
class Solution {
public:
    bool exist(vector<vector<char>> &board, string word) {
        const int m = board.size(); //行数
        const int n = board[0].size();  //列数
        vector<vector<bool>> visited(m, vector<bool>(n, false));//将访问标记数组置空
        for(int i = 0; i < m; i++)
            for(int j = 0; j < n; j++)
                if(find(board, word, 0, i, j, visited))
                    return true;                      
        return false;
    }
    static bool find(vector<vector<char>> &board, string word, int index, int x, int y, vector<vector<bool>>& visited)//辅助函数，自定义参数,看字符串是否可以找到
    {
        if(index == word.size())    //单词大小和索引相等即匹配
                                    //当单词为空的时候是满足的
                                    //下一个要查找的索引和单词大小相等说明，
                                    //word的0 - index的位置的字母已经匹配
            return true;
        if(x < 0 || y < 0 || x >= board.size() || y >= board[0].size()) //不能越界
            return false;
        if(visited[x][y]) //如果之前访问过，那么直接返回false
            return false;
        if(board[x][y] != word[index]) //不相等，这条路走不通，剪枝
            return false;
        visited[x][y] = true; //先标记为走过，因为下一次会走向四个方向
        bool ret = dfs(board, word, index + 1, x, y + 1, visited) ||
                dfs(board, word, index + 1, x, y - 1, visited)    ||
                dfs(board, word, index + 1, x - 1, y, visited)     || 
                dfs(board, word, index + 1, x + 1, y, visited); 
        visited[x][y] = false;  //走过之后，不过不匹配，要还原为没有走过
        return ret;
    }
};
```
