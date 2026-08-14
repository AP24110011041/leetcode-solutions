# 3349. Maximum Length Substring With Two Occurrences
  
<br>**Problem:** https://leetcode.com/problems/maximum-length-substring-with-two-occurrences/<br>

**Difficulty:** Easy<br>
**Topics:** Hash Table, String, Sliding Window<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-14 21:23 local time

**Runtime:** 3 ms (beats 76.1606%)
**Memory:** 19.3 MB (beats 21.079100000000004%)


<!-- leetgit:submissionId=2106772146 codeHash=d7adadad3fcf88fa0ca7554cdf06c77ff40dbb98f444b0a245cf84481623a6fb notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maximumLengthSubstring(self, s: str) -> int:
        res = l = 0
        fq = defaultdict(int)

        for r, ch in enumerate(s):
            fq[ch] += 1
            while fq[ch] > 2:
                fq[s[l]] -= 1
                l += 1
                
            res = max(res, r - l + 1)

        return res
```
