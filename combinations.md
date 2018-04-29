# Combinations
## problem
Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

Example:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
##编程实现
```C++
vector<vector<int>> combine(int n, int k) 
{
    vector<vector<int>> result;
    vector<int> solution;
    dfs(result, solution, n, k, 1);
    
    return result;
}

void dfs(vector<vector<int>>& result, vector<int>& solution, int n, int k, int start)
{
    if (solution.size() == k)
    {
        result.push_back(solution);
        return;
    }
    
    for (int i = start; i <= n; i++)
    {
        solution.push_back(i);
        dfs(result, solution, n, k, i + 1);
        solution.pop_back();
    }
}
```
