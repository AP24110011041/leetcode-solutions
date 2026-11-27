# 3625. Stone Removal Game
  
<br>**Problem:** https://leetcode.com/problems/stone-removal-game/<br>

**Difficulty:** Easy<br>
**Topics:** Math, Simulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-27 08:37 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 25.480799999999995%)


<!-- leetgit:submissionId=2204272878 codeHash=f98b35cf164cf2e49d23e8e2cba47f23dba2e2c7f19cc9cb2af18fc70fafc779 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def canAliceWin(self, n: int) -> bool:
        return (0x61F03F807FC00 >> n & 1) == 1
```
