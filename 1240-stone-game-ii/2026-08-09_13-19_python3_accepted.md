# 1240. Stone Game II
  
<br>**Problem:** https://leetcode.com/problems/stone-game-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math, Dynamic Programming, Minimax, Prefix Sum, Game Theory, Zero-Sum Game<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-09 13:19 local time

**Runtime:** 67 ms (beats 94.78439999999999%)
**Memory:** 26.1 MB (beats 49.14780000000003%)


<!-- leetgit:submissionId=2100075731 codeHash=09208e9e11fbc8efab9bd591f91aba8c8c0633a78e548817522c4004672620de notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def stoneGameII(self, piles: List[int]) -> int:
        for i in range(len(piles) - 2, -1, -1):
            piles[i] += piles[i + 1]

        @cache
        def dfs(i, M):
            if i + M * 2 >= len(piles):
                return piles[i]

            return piles[i] - min(dfs(i + j, max(M, j)) for j in range(1, M * 2 + 1))

        return dfs(0, 1)
```
