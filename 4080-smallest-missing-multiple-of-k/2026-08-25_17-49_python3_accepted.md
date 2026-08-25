# 4080. Smallest Missing Multiple of K
  
<br>**Problem:** https://leetcode.com/problems/smallest-missing-multiple-of-k/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Hash Table<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-25 17:49 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 53.3499%)


<!-- leetgit:submissionId=2119619349 codeHash=07eb6c03538c55a1cc6a5dfe7a24eead1d9bbec00d71573cd095699df36531d5 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def missingMultiple(self, nums: List[int], k: int) -> int:
        seen = set(nums)

        cur = k
        while cur in seen:
            cur += k

        return cur
```
