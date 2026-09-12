# 3562. Maximum Score of Non-overlapping Intervals
  
<br>**Problem:** https://leetcode.com/problems/maximum-score-of-non-overlapping-intervals/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Binary Search, Dynamic Programming, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-12 22:27 local time

**Runtime:** 1662 ms (beats 30.509099999999986%)
**Memory:** 86.3 MB (beats 35.593799999999995%)


<!-- leetgit:submissionId=2139809043 codeHash=3bfeb5ed5468cc60ef9b1868f9c73cc5f68e28c3da668fc936593e83dab5b2ac notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maximumWeight(self, intervals: List[List[int]]) -> List[int]:
        # Store as (end, start, weight, originalIndex) and sort by end boundary
        sortedIntervals = [(r, l, weight, i) for i, (l, r, weight) in enumerate(intervals)]
        sortedIntervals.sort(key=lambda x: x[0])

        # dp[i][j] stores a tuple: (-max_weight, lexicographically_smallest_indices)
        dp = [[(0, []) for _ in range(5)] for _ in range(len(intervals) + 1)]

        for i, (end, start, weight, originalIndex) in enumerate(sortedIntervals):
            # Binary search to find the latest non-overlapping interval
            # bisect_left finds the first interval whose end >= current start
            k = bisect_left(sortedIntervals, (start,), hi=i)
            
            for j in range(1, 5):
                prevWeight, prevIndices = dp[k][j - 1]
                
                skip = dp[i][j]
                
                # min() naturally prioritizes the lowest (most negative) weight sum, 
                # then lexicographically smallest sorted indices
                takeWeight = prevWeight - weight
                takeIndices = sorted(prevIndices + [originalIndex])
                take = (takeWeight, takeIndices)
                
                dp[i + 1][j] = min(skip, take)

        return dp[-1][4][1]
```
