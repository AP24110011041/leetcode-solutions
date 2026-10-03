# 32. Longest Valid Parentheses
  
<br>**Problem:** https://leetcode.com/problems/longest-valid-parentheses/<br>

**Difficulty:** Hard<br>
**Topics:** String, Dynamic Programming, Stack, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-03 12:37 local time

**Runtime:** 9 ms (beats 52.472699999999996%)
**Memory:** 20.5 MB (beats 66.92120000000003%)


<!-- leetgit:submissionId=2160826488 codeHash=ffef8f0f6ea9b78e9027a55840358b7a14bdfc31dcf865a360667ff8b561f1f3 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        st = [-1]
        res = 0

        for i, ch in enumerate(s):
            if ch == '(':
                st.append(i)
            else:
                st.pop()
                if not st:
                    st.append(i)
                else:
                    res = max(res, i - st[-1])

        return res
```
