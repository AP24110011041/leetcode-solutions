# 22. Generate Parentheses
  
<br>**Problem:** https://leetcode.com/problems/generate-parentheses/<br>

**Difficulty:** Medium<br>
**Topics:** String, Dynamic Programming, Backtracking, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-02 11:46 local time

**Runtime:** 3 ms (beats 30.518599999999996%)
**Memory:** 19.3 MB (beats 74.7977%)


<!-- leetgit:submissionId=2159848852 codeHash=f1fefc9403320f36677b917c583c037fdb6922dc4f0000143320c203b41fc5fd notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def generateParenthesis(self, n: int) -> list[str]:
        ans = []

        def backtrack(s: str, open: int, close: int):
            if len(s) == 2 * n:
                ans.append(s)
                return

            if open < n:
                backtrack(s + "(", open + 1, close)

            if close < open:
                backtrack(s + ")", open, close + 1)

        backtrack("", 0, 0)

        return ans
```
