# 3823. Count Islands With Total Value Divisible by K
  
<br>**Problem:** https://leetcode.com/problems/count-islands-with-total-value-divisible-by-k/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Depth-First Search, Breadth-First Search, Union-Find, Matrix<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-26 12:34 local time

**Runtime:** 316 ms (beats 65.51759999999979%)
**Memory:** 52.4 MB (beats 53.448499999999825%)


<!-- leetgit:submissionId=2181999013 codeHash=223193818c0e9b81b8144ecb8bafb1c0d87be2f9e687ebe94d03ac886528cfe0 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def countIslands(self, grid: List[List[int]], k: int) -> int:
        m, n = len(grid), len(grid[0])
        ans = 0
        def dfs(i: int, j: int) -> int:
            if i < 0 or i >= m or j < 0 or j >= n or grid[i][j] == 0:
                return 0
            s = grid[i][j]
            grid[i][j] = 0
            s += dfs(i + 1, j)
            s += dfs(i - 1, j)
            s += dfs(i, j + 1)
            s += dfs(i, j - 1)
            return s
        for i in range(m):
            for j in range(n):
                if grid[i][j] > 0:
                    if dfs(i, j) % k == 0:
                        ans += 1
        return ans
```
