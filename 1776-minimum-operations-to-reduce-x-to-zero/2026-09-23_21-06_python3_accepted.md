# 1776. Minimum Operations to Reduce X to Zero
  
<br>**Problem:** https://leetcode.com/problems/minimum-operations-to-reduce-x-to-zero/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, Binary Search, Sliding Window, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-23 21:06 local time

**Runtime:** 83 ms (beats 61.10660000000003%)
**Memory:** 30.9 MB (beats 71.3588%)


<!-- leetgit:submissionId=2151049889 codeHash=8dc0e4cb6e1260124b536bcdbb574d75960e0c0b02ad66dcdd087f3258199bd7 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minOperations(self, A: List[int], x: int) -> int:
        k = sum(A) - x
        if k < 0: return -1 
        best = -1
        
        s = i = 0
        
        for j, num in enumerate(A):
            s += num
            while s > k:
                s -= A[i]
                i += 1  
            if s == k:
                best = max(best, j - i + 1)

        return -1 if best < 0 else len(A) - best

```
