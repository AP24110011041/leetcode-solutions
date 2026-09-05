# 4285. Smallest Stable Index II
  
<br>**Problem:** https://leetcode.com/problems/smallest-stable-index-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-05 19:32 local time

**Runtime:** 125 ms (beats 92.72800000000007%)
**Memory:** 33.2 MB (beats 23.63649999999999%)


<!-- leetgit:submissionId=2131782948 codeHash=1438bc514090fc06d9b567dc86ca95d46be54de4380a09675f473db8302ee1de notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def firstStableIndex(self, A: List[int], k: int) -> int:
        msf = -1
        cand = cm = 0

        for i, x in enumerate(A):
            msf = max(msf, x)

            if i == cand:
                cm = msf

            if x < cm - k:
                cand = i + 1

        return cand if cand < len(A) else -1
```
