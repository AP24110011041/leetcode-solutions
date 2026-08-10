# 1617. Stone Game IV
  
<br>**Problem:** https://leetcode.com/problems/stone-game-iv/<br>

**Difficulty:** Hard<br>
**Topics:** Math, Dynamic Programming, Minimax, Game Theory, Nim Game, Sprague–Grundy Theorem, Zero-Sum Game<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-10 08:13 local time

**Runtime:** 1123 ms (beats 35.15420000000037%)
**Memory:** 161.8 MB (beats 9.09230000000002%)


<!-- leetgit:submissionId=2100960381 codeHash=dab2ef81ea9d48f997cb9fa2a2b9df741fda06e24e27eca2cd2edebe333718d9 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def winnerSquareGame(self, n: int) -> bool:
        @cache
        def dfs(i):
            if i == 0: return False

            for j in range(1, isqrt(i) + 1):
                if not dfs(i - j ** 2): return True

            return False

        return dfs(n)
```
