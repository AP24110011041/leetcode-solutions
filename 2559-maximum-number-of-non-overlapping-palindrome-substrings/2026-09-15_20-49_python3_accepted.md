# 2559. Maximum Number of Non-overlapping Palindrome Substrings
  
<br>**Problem:** https://leetcode.com/problems/maximum-number-of-non-overlapping-palindrome-substrings/<br>

**Difficulty:** Hard<br>
**Topics:** Two Pointers, String, Dynamic Programming, Greedy<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-15 20:49 local time

**Runtime:** 3 ms (beats 95.8763%)
**Memory:** 19.3 MB (beats 88.6598%)


<!-- leetgit:submissionId=2142737253 codeHash=32882345c2202b7497df257e7f0f3c359cc8f881c140d4f970094b2e058cc041 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxPalindromes(self, s: str, k: int) -> int:
        n = len(s)
        if k == 1: return n

        res = i = 0

        while i <= n - k:
            for d in (k, k + 1):
                if i + d <= n and s[i : i + d] == s[i : i + d][::-1]:
                    res += 1
                    i += d
                    break
            else:
                i += 1

        return res
```
