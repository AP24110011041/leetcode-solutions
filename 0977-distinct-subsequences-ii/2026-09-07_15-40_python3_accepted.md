# 977. Distinct Subsequences II
  
<br>**Problem:** https://leetcode.com/problems/distinct-subsequences-ii/<br>

**Difficulty:** Hard<br>
**Topics:** String, Dynamic Programming<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-07 15:40 local time

**Runtime:** 3455 ms (beats 5.208900000000006%)
**Memory:** 19.3 MB (beats 72.39579999999998%)


<!-- leetgit:submissionId=2133758212 codeHash=1bdb1e85876f3a5ddc68797995c8689b64e3882b2426835c83abb301e868f35b notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def distinctSubseqII(self, s):
        n = len(s)
        MOD = 10**9 + 7

        dp = [1] * n
        result = 0

        for i in range(n):

            for j in range(i):
                if s[i] != s[j]:
                    dp[i] = (dp[i] + dp[j]) % MOD

            result = (result + dp[i]) % MOD

        return result
```
