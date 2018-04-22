## problem
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.

Each number in candidates may only be used once in the combination.

Note:

All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8,
A solution set is:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
Example 2:

Input: candidates = [2,5,2,1,2], target = 5,
A solution set is:
[
  [1,2,2],
  [5]
]
## 代码实现
```C++
vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
    vector<vector<int>> res;
    vector<int> tmp;
    sort(candidates.begin(),candidates.end());
    backTracking(candidates.begin(),current,res,candidates,target);
    return res;
}

void getVector(vector<int>::iterator n, vector<int>& tmp,vector<vector<int>>& res, const vector<int>& candidates, int target){
    if(!target) res.push_back(tmp);
    else if(target>0){
        for(;n!=candidates.end()&&*n<=target;++n){
            current.push_back(*n);
            getVector(n+1,tmp,res,candidates,target-*n);
            current.pop_back();
            while(n+1!=candidates.end()&&*(n+1)==*n) ++n;
        }
    }
}
```
