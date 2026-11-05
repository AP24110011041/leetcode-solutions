# 1486. Find the Distance Value Between Two Arrays
  
<br>**Problem:** https://leetcode.com/problems/find-the-distance-value-between-two-arrays/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Two Pointers, Binary Search, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-05 23:27 local time

**Runtime:** 4 ms (beats 92.2308%)
**Memory:** 19.3 MB (beats 69.9223%)


<!-- leetgit:submissionId=2190267822 codeHash=626df7deb86f91eab7c82583021c082e377a1777315c4087e6c7a3dc47c68573 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def findTheDistanceValue(self, arr1: List[int], arr2: List[int], d: int) -> int:
        arr2 = sorted(arr2) + [inf]  # sentinel: the pointer never runs off the end
        j = 0

        def far(a):  # a only grows, so the first b >= a - d only moves right
            nonlocal j
            while arr2[j] < a - d:
                j += 1
            return arr2[j] > a + d

        return sum(map(far, sorted(arr1)))
```
