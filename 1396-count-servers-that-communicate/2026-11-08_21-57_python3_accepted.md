# 1396. Count Servers that Communicate
  
<br>**Problem:** https://leetcode.com/problems/count-servers-that-communicate/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Depth-First Search, Breadth-First Search, Union-Find, Matrix, Counting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-08 21:57 local time

**Runtime:** 15 ms (beats 77.9659%)
**Memory:** 21.2 MB (beats 97.7401%)


<!-- leetgit:submissionId=2192013951 codeHash=a690c20d3771ec26568c4e4d07d14f4b4b85b848473930ab8bdd2c323722adda notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def countServers(self, grid: list[list[int]]) -> int:
        rows = [sum(row) for row in grid]  # servers on each row
        cols = [sum(col) for col in zip(*grid)]  # servers on each column

        ans = 0
        for i, row in enumerate(grid):
            for j, server in enumerate(row):
                if server and rows[i] + cols[j] > 2:  # it's counted in both, so more than 2 means company
                    ans += 1
        return ans
```
