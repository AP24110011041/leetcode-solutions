# 3918. Check Divisibility by Digit Sum and Product
  
<br>**Problem:** https://leetcode.com/problems/check-divisibility-by-digit-sum-and-product/<br>

**Difficulty:** Easy<br>
**Topics:** Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-22 14:52 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 91.314%)


<!-- leetgit:submissionId=2115952521 codeHash=119efbe51609cd36213682b99f000cf794148f1fb3167e0f29777295906c462d notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def checkDivisibility(self, n: int) -> bool:
        s, p, x=0, 1, n
        while x>0:
            x, r=divmod(x, 10)
            s+=r
            p*=r
        return n%(s+p)==0
```
