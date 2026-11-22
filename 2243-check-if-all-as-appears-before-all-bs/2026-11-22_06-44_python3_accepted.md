# 2243. Check if All A's Appears Before All B's
  
<br>**Problem:** https://leetcode.com/problems/check-if-all-as-appears-before-all-bs/<br>

**Difficulty:** Easy<br>
**Topics:** String<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-22 06:44 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.4 MB (beats 6.813099999999999%)


<!-- leetgit:submissionId=2200881508 codeHash=0cc4a05cd1a544b8d209bf88d09f4cf282abea721f2435253973696158fe171e notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def checkString(self, s: str) -> bool:
        return "ba" not in s
```
