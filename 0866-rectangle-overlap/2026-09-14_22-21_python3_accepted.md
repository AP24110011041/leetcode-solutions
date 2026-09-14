# 866. Rectangle Overlap
  
<br>**Problem:** https://leetcode.com/problems/rectangle-overlap/<br>

**Difficulty:** Easy<br>
**Topics:** Math, Geometry<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-14 22:21 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.4 MB (beats 19.52950000000002%)


<!-- leetgit:submissionId=2141791804 codeHash=9ed8ffe0d7f9f6fea054931ad2c4bf43e2352936e9cb77dba856931f1b3384ed notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def isRectangleOverlap(self, *A) -> bool:
        (x1, y1, x2, y2), (X1, Y1, X2, Y2) = A
        return x1 < X2 and X1 < x2 and y1 < Y2 and Y1 < y2
```
