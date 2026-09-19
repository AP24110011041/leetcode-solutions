# 1501. Circle and Rectangle Overlapping
  
<br>**Problem:** https://leetcode.com/problems/circle-and-rectangle-overlapping/<br>

**Difficulty:** Medium<br>
**Topics:** Math, Geometry<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-19 12:35 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 49.3333%)


<!-- leetgit:submissionId=2146402521 codeHash=5d494648a5b1a5ca1230f9b7e4a9bb1589c12640b7f55d6116e7a9cb84789ef2 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def checkOverlap(self, r: int, cx: int, cy: int, x1: int, y1: int, x2: int, y2: int) -> bool:
        x = max(x1, min(cx, x2)) - cx
        y = max(y1, min(cy, y2)) - cy

        return x * x + y * y <= r * r
```
