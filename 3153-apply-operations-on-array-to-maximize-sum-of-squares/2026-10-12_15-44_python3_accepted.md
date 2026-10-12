# 3153. Apply Operations on Array to Maximize Sum of Squares
  
<br>**Problem:** https://leetcode.com/problems/apply-operations-on-array-to-maximize-sum-of-squares/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Hash Table, Greedy, Bit Manipulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-12 15:44 local time

**Runtime:** 1290 ms (beats 76.59529999999995%)
**Memory:** 32.1 MB (beats 57.446799999999996%)


<!-- leetgit:submissionId=2170079891 codeHash=b9af9d401f3bc8078110859397d37606458e34889b4d6b9835de3d2c6a37a166 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxSum(self, nums: list[int], k: int) -> int:
        cnt = [sum(x >> b & 1 for x in nums) for b in range(30)]  # coins in each bit column, never changes
        total = 0
        for i in range(k):  # build row i of the stacked picture
            row = sum(1 << b for b in range(30) if cnt[b] > i)  # a coin from every column with more than i coins
            total += row * row
        return total % (10**9 + 7)
```
