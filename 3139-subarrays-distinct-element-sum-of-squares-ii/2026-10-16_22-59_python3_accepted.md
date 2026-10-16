# 3139. Subarrays Distinct Element Sum of Squares II
  
<br>**Problem:** https://leetcode.com/problems/subarrays-distinct-element-sum-of-squares-ii/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Hash Table, Binary Indexed Tree, Segment Tree<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-16 22:59 local time

**Runtime:** 674 ms (beats 100%)
**Memory:** 39.8 MB (beats 96.5517%)


<!-- leetgit:submissionId=2174037216 codeHash=0efe3ba32ee116696a19af1810fee27e3d70bf8ae635bb8369d3a05d05c65f4a notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def sumCounts(self, nums: List[int]) -> int:
        n = len(nums)
        cnt, tot = [0] * (n + 1), [0] * (n + 1)  # Fenwick trees over previous-copy positions, stored right to left
        last, ans = {}, 0
        for r, x in enumerate(nums):
            p = last.get(x, -1)
            c = s = 0
            i = n - p - 1  # boxes 1..n-p-1 hold the positions > p
            while i:
                c += cnt[i]
                s += tot[i]
                i -= i & -i
            ans += (n - r) * ((r - p) ** 2 - 2 * (s - p * c))
            i = n - p  # insert p; p = -1 lands past the end and is skipped
            while i <= n:
                cnt[i] += 1
                tot[i] += p
                i += i & -i
            last[x] = r
        return ans % (10**9 + 7)
```
