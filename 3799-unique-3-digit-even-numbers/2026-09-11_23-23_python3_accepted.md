# 3799. Unique 3-Digit Even Numbers
  
<br>**Problem:** https://leetcode.com/problems/unique-3-digit-even-numbers/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Hash Table, Recursion, Enumeration<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-11 23:23 local time

**Runtime:** 80 ms (beats 19.56009999999999%)
**Memory:** 19.3 MB (beats 38.461600000000004%)


<!-- leetgit:submissionId=2138836021 codeHash=d15f698f7c1aa2d6e2da6e09edbeabf421080b663a7fd5dd698d9d2c8df11b4a notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def totalNumbers(self, digits: List[int]) -> int:
        f = Counter(digits)

        res = 0
        for n in range(100, 1000, 2):
            i, r = divmod(n, 100)
            j, k = divmod(r, 10)
            res += f[i] > 0 and f[j] > (i == j) and f[k] > (i == k) + (j == k)

        return res
```
