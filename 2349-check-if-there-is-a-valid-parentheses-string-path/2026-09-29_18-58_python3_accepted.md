# 2349.  Check if There Is a Valid Parentheses String Path
  
<br>**Problem:** https://leetcode.com/problems/check-if-there-is-a-valid-parentheses-string-path/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Dynamic Programming, Matrix, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-29 18:58 local time

**Runtime:** 15 ms (beats 84%)
**Memory:** 29.8 MB (beats 72%)


<!-- leetgit:submissionId=2157117534 codeHash=f100b064157635946b28b772f2ab2521acf713dcea5ae9b136d2587a40d2d832 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def hasValidPath(self, A: list[list[str]]) -> bool:
        m, n = len(A), len(A[0])

        if ~(m + n) & 1 or A[0][0] == ")" or A[-1][-1] == "(":
            return False

        @cache
        def dfs(i, j, x):
            x += 1 - ((ord(A[i][j]) & 1) << 1)

            if x < 0 or x > (m + n - 1) - (i + j):
                return False

            if i == m - 1 and j == n - 1:
                return x == 0

            return (i < m - 1 and dfs(i + 1, j, x)) or \
                   (j < n - 1 and dfs(i, j + 1, x))

        return dfs(0, 0, 0)
```
