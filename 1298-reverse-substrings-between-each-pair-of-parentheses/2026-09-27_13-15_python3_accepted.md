# 1298. Reverse Substrings Between Each Pair of Parentheses
  
<br>**Problem:** https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses/<br>

**Difficulty:** Medium<br>
**Topics:** String, Stack, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-27 13:15 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 69.69699999999999%)


<!-- leetgit:submissionId=2154744708 codeHash=42b049469fce8da82280b5b0115ad3393c646437688a9a90a333bfcd592335d1 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def reverseParentheses(self, s: str) -> str:
        n = len(s)
        link = [0] * n
        stk = res = []

        for i, c in enumerate(s):
            if c == '(':
                stk.append(i)
            elif c == ')':
                j = stk.pop()
                link[i] = j
                link[j] = i

        dr, i = 1, 0
        while i < n:
            if s[i] >= 'a':
                res.append(s[i])
            else:
                i = link[i]
                dr = -dr

            i += dr

        return ''.join(res)
```
