# 2039. Sum Game
  
<br>**Problem:** https://leetcode.com/problems/sum-game/<br>

**Difficulty:** Medium<br>
**Topics:** Math, String, Greedy, Game Theory<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-23 16:35 local time

**Runtime:** 63 ms (beats 32.94149999999996%)
**Memory:** 19.8 MB (beats 65.2941%)


<!-- leetgit:submissionId=2117251131 codeHash=30eea5596b4c5ae8e58342fe3ed6252245b48b19a1b73d83d6bad336091c48b0 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def sumGame(self, num: str) -> bool:
        n = len(num)
        q_cnt_1 = s1 = 0
        for i in range(n//2):    # get digit sum and question mark count for the first half of `num`
            if num[i] == '?':
                q_cnt_1 += 1
            else:    
                s1 += int(num[i])
        q_cnt_2 = s2 = 0				
        for i in range(n//2, n): # get digit sum and question mark count for the second half of `num`
            if num[i] == '?':
                q_cnt_2 += 1
            else:    
                s2 += int(num[i])
        s_diff = s1 - s2         # calculate sum difference and question mark difference
        q_diff = q_cnt_2 - q_cnt_1
        return not (q_diff % 2 == 0 and q_diff // 2 * 9 == s_diff) # When Bob can't win, Alice wins
```
