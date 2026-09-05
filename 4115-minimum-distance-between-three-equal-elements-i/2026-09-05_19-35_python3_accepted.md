# 4115. Minimum Distance Between Three Equal Elements I
  
<br>**Problem:** https://leetcode.com/problems/minimum-distance-between-three-equal-elements-i/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Hash Table<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-05 19:35 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 27.916099999999986%)


<!-- leetgit:submissionId=2131785877 codeHash=d0323dae93b76d6a391d2ab9dadccfe6a291ec4f475b20d4bcf5b96bb7973a20 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minimumDistance(self, nums: List[int]) -> int:
        n = len(nums)
        last2 = [0] * n
        res = 200

        for i in range(n):
            val, pos = nums[i] - 1, i + 1
            pack = last2[val]
            old, cur = pack & 255, pack >> 8

            last2[val] = cur | (pos << 8)

            if old:
                res = min(res, (pos - old) << 1)

        return -(res == 200) | res
```
