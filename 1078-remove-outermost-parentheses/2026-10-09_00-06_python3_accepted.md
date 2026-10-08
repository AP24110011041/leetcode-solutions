# 1078. Remove Outermost Parentheses
  
<br>**Problem:** https://leetcode.com/problems/remove-outermost-parentheses/<br>

**Difficulty:** Easy<br>
**Topics:** String, Stack, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-09 00:06 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 70.87429999999999%)


<!-- leetgit:submissionId=2166667138 codeHash=104ffd42db33ab59a5d235ec089b545d708cc658b80b60073d61b776b1194aa5 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def removeOuterParentheses(self, s: str) -> str:
        res, lvl = [], 0

        for c in s:
            if c == ")":
                lvl -= 1
            if lvl > 0:
                res.append(c)
            if c == "(":
                lvl += 1
                
        return "".join(res)
```
