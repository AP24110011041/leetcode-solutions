# 3174. Minimum Number of Changes to Make Binary String Beautiful
  
<br>**Problem:** https://leetcode.com/problems/minimum-number-of-changes-to-make-binary-string-beautiful/<br>

**Difficulty:** Medium<br>
**Topics:** String<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-19 01:15 local time

**Runtime:** 16 ms (beats 84.21050000000001%)
**Memory:** 19.9 MB (beats 17.76310000000001%)


<!-- leetgit:submissionId=2198935403 codeHash=791015a653c687b77ba1f5a61fcb4742896b9b53ab5b79da4695ff1488e4fd02 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minChanges(self, s: str) -> int:
        return sum(a != b for a, b in batched(s, 2))
```
