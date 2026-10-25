# 1380. Number of Closed Islands
  
<br>**Problem:** https://leetcode.com/problems/number-of-closed-islands/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Depth-First Search, Breadth-First Search, Union-Find, Matrix<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-25 11:17 local time

**Runtime:** 12 ms (beats 87.91290000000001%)
**Memory:** 20 MB (beats 53.52839999999999%)


<!-- leetgit:submissionId=2181123571 codeHash=451e6d0b20d3c42bc9a7a254f60be83d82dc7cc06a25e4bb8d25d32743e00fa8 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def closedIsland(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])

        def closed(i, j):  # flood the island through (i, j); True if it never reaches the border
            if not (0 <= i < m and 0 <= j < n):
                return False  # stepped off the grid: the island touches the border
            if grid[i][j]:
                return True  # water, or land we already flooded
            grid[i][j] = 1  # visited: turn it into water
            return closed(i + 1, j) & closed(i - 1, j) & closed(i, j + 1) & closed(i, j - 1)  # & (not and) floods all 4 sides

        return sum(closed(i, j) for i in range(m) for j in range(n) if not grid[i][j])
```
