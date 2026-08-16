# 2156. Stone Game IX
  
<br>**Problem:** https://leetcode.com/problems/stone-game-ix/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math, Greedy, Minimax, Counting, Game Theory, Nim Game, Zero-Sum Game<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-16 17:25 local time

**Runtime:** 43 ms (beats 88.54959999999998%)
**Memory:** 30.5 MB (beats 61.06859999999998%)


<!-- leetgit:submissionId=2108932749 codeHash=b1420cb55434a613d568413400a1e45a541aff81d67f6087b450e39b21a7ebf9 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def stoneGameIX(self, stones: List[int]) -> bool:
        f = [0, 0, 0]

        for s in stones:
            f[s % 3] += 1

        if ~f[0] & 1:
            return min(f[1], f[2]) >= 1

        return abs(f[1] - f[2]) >= 3
```
