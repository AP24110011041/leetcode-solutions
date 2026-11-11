# 4147. Minimum Cost to Acquire Required Items
  
<br>**Problem:** https://leetcode.com/problems/minimum-cost-to-acquire-required-items/<br>

**Difficulty:** Medium<br>
**Topics:** Math, Greedy<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-12 02:36 local time

**Runtime:** 1 ms (beats 38.1443%)
**Memory:** 19.3 MB (beats 25.773199999999996%)


<!-- leetgit:submissionId=2194178894 codeHash=6a3eec7525b610a4f784ebe5dfb5952a7d421796d99809b30faaca269c2acf51 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minimumCost(self, cost1: int, cost2: int, costBoth: int, need1: int, need2: int) -> int:
        both = min(need1, need2)
        return (both * min(cost1 + cost2, costBoth)  # pair or bundle
                + (need1 - both) * min(cost1, costBoth)  # single or bundle
                + (need2 - both) * min(cost2, costBoth))
```
