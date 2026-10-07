# 301. Remove Invalid Parentheses
  
<br>**Problem:** https://leetcode.com/problems/remove-invalid-parentheses/<br>

**Difficulty:** Hard<br>
**Topics:** String, Backtracking, Breadth-First Search<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-07 21:02 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 99.02479999999998%)


<!-- leetgit:submissionId=2165441161 codeHash=3e15c9d15102cb15ca62f39229b360dddb1a6e9fa6d4466e56192f4557fb79f6 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:  # Iterative
    def removeInvalidParentheses(self, s: str) -> List[str]:
        res = []
        stack = [(s, 0, 0, ("(", ")"))]

        while stack:
            cur, li, lj, par = stack.pop()
            n = len(cur)
            bal = 0
            match = False

            for i in range(li, n):
                bal += (cur[i] == par[0]) - (cur[i] == par[1])
                if bal >= 0:
                    continue

                for j in range(lj, i + 1):
                    if cur[j] == par[1] and (j == lj or cur[j - 1] != par[1]):
                        nxt = cur[:j] + cur[j + 1 :]
                        stack.append((nxt, i, j, par))

                match = True
                break

            if not match:
                rev = cur[::-1]

                if par[0] == "(":
                    stack.append((rev, 0, 0, (")", "(")))
                else:
                    res.append(rev)

        return res
```
