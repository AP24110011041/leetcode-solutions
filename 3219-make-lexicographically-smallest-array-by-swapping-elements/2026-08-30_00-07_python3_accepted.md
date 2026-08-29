# 3219. Make Lexicographically Smallest Array by Swapping Elements
  
<br>**Problem:** https://leetcode.com/problems/make-lexicographically-smallest-array-by-swapping-elements/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Union-Find, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-30 00:07 local time

**Runtime:** 227 ms (beats 88.80579999999993%)
**Memory:** 53.1 MB (beats 44.02949999999989%)


<!-- leetgit:submissionId=2124255724 codeHash=b63844ce1b8545d8a28f827d1ab6e8be500e229b6a4f86b0e1f2971f495bfd24 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def lexicographicallySmallestArray(self, nums, limit):
        n = len(nums)

        sorted_nums = sorted(nums)

        group = {}
        groupId = {}
        pos = {}

        id = 1
        group[id] = [sorted_nums[0]]
        groupId[sorted_nums[0]] = id

        for i in range(1, n):
            if sorted_nums[i] - sorted_nums[i - 1] > limit:
                id += 1

            group.setdefault(id, []).append(sorted_nums[i])
            groupId[sorted_nums[i]] = id

        # Rebuild nums using the smallest
        # available value from its group
        for i in range(n):
            grp = groupId[nums[i]]
            p = pos.get(grp, 0)

            nums[i] = group[grp][p]
            pos[grp] = p + 1

        return nums
```
