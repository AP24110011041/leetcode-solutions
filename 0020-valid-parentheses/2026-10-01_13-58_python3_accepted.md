# 20. Valid Parentheses
  
<br>**Problem:** https://leetcode.com/problems/valid-parentheses/<br>

**Difficulty:** Easy<br>
**Topics:** String, Stack, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-01 13:58 local time

**Runtime:** 3 ms (beats 32.7678%)
**Memory:** 19.2 MB (beats 64.57119999999998%)


<!-- leetgit:submissionId=2159003382 codeHash=810ace6ae27e0069c21deb760b1ba6db59cee4db6124a89c0771d49b5e4a5f41 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for ch in s:
            if ch in '([{':
                stack.append(ch)
            else:
                if not stack:
                    return False
                top = stack.pop()
                if ch == ')' and top != '(':
                    return False
                if ch == ']' and top != '[':
                    return False
                if ch == '}' and top != '{':
                    return False
        return not stack
```
