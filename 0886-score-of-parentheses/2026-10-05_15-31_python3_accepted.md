# 886. Score of Parentheses
  
<br>**Problem:** https://leetcode.com/problems/score-of-parentheses/<br>

**Difficulty:** Medium<br>
**Topics:** String, Stack, Bracket Sequences<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-05 15:31 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 55.73100000000001%)


<!-- leetgit:submissionId=2162992760 codeHash=a185d97fd9cfcdf92d54c187c381063fac0678556573aa905eee435062f0e8b5 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def scoreOfParentheses(self, s: str) -> int:
        stack = [0]

        for ch in s:
            if ch == '(':
                stack.append(0)
            else:
                inside = stack.pop()

                if inside == 0:
                    stack.append(stack.pop() + 1)
                else:
                    stack.append(stack.pop() + 2 * inside)

        return stack.pop()
```
