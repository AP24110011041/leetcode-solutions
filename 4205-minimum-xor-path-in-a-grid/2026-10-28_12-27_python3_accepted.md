# 4205. Minimum XOR Path in a Grid
  
<br>**Problem:** https://leetcode.com/problems/minimum-xor-path-in-a-grid/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Dynamic Programming, Bit Manipulation, Matrix<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-28 12:27 local time

**Runtime:** 703 ms (beats 90.83350000000003%)
**Memory:** 25.8 MB (beats 90%)


<!-- leetgit:submissionId=2183699398 codeHash=2ab3d062890981a969c27b1ffcea4a89690672d5ea9d8c77acc4595366666ef3 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minCost(self, grid: list[list[int]]) -> int:
        dp = [{0}] + [set() for _ in range(len(grid[0]) - 1)]  # dp[j]: every XOR that can reach column j of the row above
        for row in grid:
            for j, v in enumerate(row):
                dp[j] = {x ^ v for x in dp[j] | (dp[j - 1] if j else set())}  # come from above or from the left
        return min(dp[-1])
```
