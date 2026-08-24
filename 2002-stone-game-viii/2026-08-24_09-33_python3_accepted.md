# 2002. Stone Game VIII
  
<br>**Problem:** https://leetcode.com/problems/stone-game-viii/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Math, Dynamic Programming, Minimax, Prefix Sum, Game Theory, Zero-Sum Game<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-24 09:33 local time

**Runtime:** 912 ms (beats 8.28589999999991%)
**Memory:** 250 MB (beats 5.325799999999968%)


<!-- leetgit:submissionId=2117972499 codeHash=bdd938b3f6f5a03c41f6246532179e890d02d62d632181f82493b7ea2a9e1d9f notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def stoneGameVIII(self, A: List[int]) -> int:
        n = len(A)
        s = list(accumulate(A))

        @cache
        def maxDiff(i):
            if i == n - 1: return s[n - 1]
            return max(maxDiff(i + 1), s[i] - maxDiff(i + 1))

        return maxDiff(1)
```
