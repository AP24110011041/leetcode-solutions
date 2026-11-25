# 4105. Smallest Unique Subarray
  
<br>**Problem:** https://leetcode.com/problems/smallest-unique-subarray/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Hash Table, Binary Search, Rolling Hash, Suffix Array, Hash Function<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-26 00:05 local time

**Runtime:** 2187 ms (beats 54.54499999999993%)
**Memory:** 103.2 MB (beats 7.272000000000003%)


<!-- leetgit:submissionId=2203442593 codeHash=4db47f484680195cc0250e819619ca69da18b4b7cc1a02868a1b12d6e2f92360 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def smallestUniqueSubarray(self, nums: list[int]) -> int:
        n = len(nums)
        names = [nums]  # names[k][i] same for equal windows nums[i:i + 2**k]
        for k in range(n.bit_length() - 1):  # blocks of 2, 4, 8, ... while they fit
            ids = {}  # pair of halves -> number of the whole window
            names.append([ids.setdefault(pair, len(ids)) for pair in zip(names[k], names[k][2 ** k:])])

        def found(length):  # is some window of this length unique?
            k = length.bit_length() - 1  # its first 2**k elements and its last 2**k cover it
            return 1 in Counter(zip(names[k], names[k][length - 2 ** k:])).values()

        return bisect_left(range(1, n), True, key=found) + 1
```
