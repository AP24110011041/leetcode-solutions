# 864. Image Overlap
  
<br>**Problem:** https://leetcode.com/problems/image-overlap/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Matrix<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-13 23:15 local time

**Runtime:** 270 ms (beats 44.44139999999993%)
**Memory:** 19.8 MB (beats 49.99990000000002%)


<!-- leetgit:submissionId=2140873080 codeHash=e129ba43fe7923b92ba35ac64d95e1fa110de50e7105fd4262f4d0ff553404d9 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def largestOverlap(self, img1, img2):
        n = len(img1)

        ones1 = [(r, c) for r in range(n) for c in range(n) if img1[r][c] == 1]
        ones2 = [(r, c) for r in range(n) for c in range(n) if img2[r][c] == 1]

        frequency = {}
        maxOverlap = 0

        for r1, c1 in ones1:
            for r2, c2 in ones2:
                dr = r1 - r2
                dc = c1 - c2

                key = (dr, dc)
                frequency[key] = frequency.get(key, 0) + 1
                maxOverlap = max(maxOverlap, frequency[key])

        return maxOverlap
```
