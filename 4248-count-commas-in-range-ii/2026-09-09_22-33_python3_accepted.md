# 4248. Count Commas in Range II
  
<br>**Problem:** https://leetcode.com/problems/count-commas-in-range-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-09 22:33 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 51.700599999999994%)


<!-- leetgit:submissionId=2136624649 codeHash=2e1c765941e555ffdcbb569b89ad55047a37293af6b5a770fae917689a47a04d notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def countCommas(self, n: int) -> int:
        count, p = 0, 1000

        while p <= n:
            count += n - p + 1
            p *= 1000

        return count
```
