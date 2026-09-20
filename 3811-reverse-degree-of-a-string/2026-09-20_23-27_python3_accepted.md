# 3811. Reverse Degree of a String
  
<br>**Problem:** https://leetcode.com/problems/reverse-degree-of-a-string/<br>

**Difficulty:** Easy<br>
**Topics:** String, Simulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-20 23:27 local time

**Runtime:** 7 ms (beats 70.0001%)
**Memory:** 19.4 MB (beats 19.1303%)


<!-- leetgit:submissionId=2147969270 codeHash=e5690eb4cae453c667255c932f01ac9196da8744eaef4a86759620a97598341e notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def reverseDegree(self, s: str) -> int:
        return sum((i+1)*(ord('z')-ord(c)+1) for i, c in enumerate(s))
```
