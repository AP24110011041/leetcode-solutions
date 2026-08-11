# 3236. Smallest Missing Integer Greater Than Sequential Prefix Sum
  
<br>**Problem:** https://leetcode.com/problems/smallest-missing-integer-greater-than-sequential-prefix-sum/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Hash Table, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-11 08:15 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 87.8935%)


<!-- leetgit:submissionId=2102192747 codeHash=8ab6176a1cd92ee097232f758c9e8e0fec6fece5e7e545db0dbb164f822f7de6 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def missingInteger(self, A: list[int]) -> int:
        n = len(A)
        seen = set(A)
        sum = A[0]

        for i in range(1, n):
            if A[i] == A[i - 1] + 1:
                sum += A[i]
            else:
                break

        while sum in seen:
            sum += 1

        return sum
        
```
