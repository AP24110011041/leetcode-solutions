# 2496. Count Days Spent Together
  
<br>**Problem:** https://leetcode.com/problems/count-days-spent-together/<br>

**Difficulty:** Easy<br>
**Topics:** Math, String<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-24 22:51 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.1 MB (beats 98.4376%)


<!-- leetgit:submissionId=2180720071 codeHash=75498cadc3759b451dbdd373d88d365245ec57ec9c8e9433c09315b44998a899 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def countDaysTogether(self, a: str, b: str, c: str, d: str) -> int:
        def f(s):
            m, q = int(s[:2]), int(s[3:])
            return (275 * m) // 9 - 2 * ((m + 9) // 12) + q - 30

        return max(0, min(f(b), f(d)) - max(f(a), f(c)) + 1)

```
