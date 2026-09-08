# 4245. Count Commas in Range
  
<br>**Problem:** https://leetcode.com/problems/count-commas-in-range/<br>

**Difficulty:** Easy<br>
**Topics:** Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-08 22:40 local time

**Runtime:** 343 ms (beats 12.97559999999999%)
**Memory:** 19.4 MB (beats 14.988900000000005%)


<!-- leetgit:submissionId=2135417603 codeHash=bd95792d7be56bbd8f3ca0880e0ed01931c15d2bfdcb350ad4753564c3301168 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution(object):
    def countCommas(self, n):
        count = 0

        for i in range(1, n + 1):
            if i >= 1000:
                count += 1

        return count
```
