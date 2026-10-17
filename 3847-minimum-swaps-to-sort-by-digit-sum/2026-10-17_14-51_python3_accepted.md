# 3847. Minimum Swaps to Sort by Digit Sum
  
<br>**Problem:** https://leetcode.com/problems/minimum-swaps-to-sort-by-digit-sum/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-17 14:51 local time

**Runtime:** 1635 ms (beats 7.960799999999846%)
**Memory:** 49.7 MB (beats 27.432499999999898%)


<!-- leetgit:submissionId=2174440756 codeHash=abd8c4c7f17450a8a457d7880702c591d1ae51d3c8b4f704d69fab0ed5953f5e notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Pair:
    def __init__(self, d, val, idx):
        self.dsum = d
        self.val = val
        self.idx = idx

class Solution:
    def digitSum(self, num):
        return sum(int(d) for d in str(num))

    def minSwaps(self, nums):
        n = len(nums)
        pairs = [Pair(self.digitSum(nums[i]), nums[i], i) for i in range(n)]

        pairs.sort(key=lambda x: (x.dsum, x.val))

        i = 0
        cnt = 0
        while i < n:
            if pairs[i].idx != i:
                cnt += 1
                j = pairs[i].idx
                pairs[i], pairs[j] = pairs[j], pairs[i]
            else:
                i += 1
        return cnt
```
