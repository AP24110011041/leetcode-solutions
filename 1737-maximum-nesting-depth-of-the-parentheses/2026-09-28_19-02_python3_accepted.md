# 1737. Maximum Nesting Depth of the Parentheses
  
<br>**Problem:** https://leetcode.com/problems/maximum-nesting-depth-of-the-parentheses/<br>

**Difficulty:** Easy<br>
**Topics:** String, Stack, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-28 19:02 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 50.4007%)


<!-- leetgit:submissionId=2156008123 codeHash=db0d72fd9e35e6c6a90bf292b68bf75b47c6e833f3c8d596c32b69fb9a873cf4 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxDepth(self, s):
        depth = 0
        r = 0
        for c in s:
            if c == ')':
                depth -= 1
                continue
            # Digits and operators
            if c != '(':
                continue
            depth += 1
            # New max only possible after '('
            if depth > r:
                r = depth
        return r
```
