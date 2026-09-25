# 1188. Brace Expansion II
  
<br>**Problem:** https://leetcode.com/problems/brace-expansion-ii/<br>

**Difficulty:** Hard<br>
**Topics:** Hash Table, String, Backtracking, Stack, Breadth-First Search, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-25 16:58 local time

**Runtime:** 23 ms (beats 5.464699999999972%)
**Memory:** 20.1 MB (beats 6.55749999999999%)


<!-- leetgit:submissionId=2152927801 codeHash=b3a08ee4d0916ec7f2440bbac710df76a7430b8a9402b39bc4bb0c5be8592190 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def braceExpansionII(self, expression):
        ans = set()

        def dfs(s):
            r = s.find('}')

            # No braces left
            if r == -1:
                ans.add(s)
                return

            # Find matching '{'
            l = s.rfind('{', 0, r)

            left = s[:l]
            right = s[r + 1:]

            # Content inside { }
            inside = s[l + 1:r]

            for part in inside.split(','):
                dfs(left + part + right)

        dfs(expression)
        return sorted(ans)
```
