# 4258. Construct Uniform Parity Array II
  
<br>**Problem:** https://leetcode.com/problems/construct-uniform-parity-array-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-03 20:06 local time

**Runtime:** 43 ms (beats 71.95069999999993%)
**Memory:** 35 MB (beats 93.90229999999998%)


<!-- leetgit:submissionId=2129716617 codeHash=d12d0133985e3e88f4cb396a313c5f4156a7d2acf327609c4b046fdd8a128611 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def uniformArray(self, A: list[int]) -> bool:
        return not (min(A) ^ reduce(or_, A)) & 1
```
