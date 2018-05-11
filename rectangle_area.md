## problem
Find the total area covered by two rectilinear rectangles in a 2D plane.

Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.

Rectangle Area

Example:

Input: -3, 0, 3, 4, 0, -1, 9, 2
Output: 45

## 解题思路
就是求面积，很简单的问题，不知道为啥是mid题
## 代码实现
```C++
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        return (D - B) * (C - A) + (H - F) * (G - E) - max(min(min(C - A, G - E),min(C - E, G - A)),0) * max(min(min(H - F, D - B),min(H - B, D - F)),0);
    }
};
```
