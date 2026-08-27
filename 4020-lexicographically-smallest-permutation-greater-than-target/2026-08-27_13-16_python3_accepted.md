# 4020. Lexicographically Smallest Permutation Greater Than Target
  
<br>**Problem:** https://leetcode.com/problems/lexicographically-smallest-permutation-greater-than-target/<br>

**Difficulty:** Medium<br>
**Topics:** Hash Table, String, Greedy, Counting, Enumeration<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-27 13:16 local time

**Runtime:** 7 ms (beats 88.15780000000001%)
**Memory:** 19.4 MB (beats 71.0527%)


<!-- leetgit:submissionId=2121651134 codeHash=3435d5036052d3bdad0735f19763abf81742e581bff7e1d4d0a9e74c16948dbd notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def lexGreaterPermutation(self, s: str, target: str) -> str:
        cnt = [0] * 26
        for i in range(len(s)):
            cnt[ord(s[i]) - ord("a")] += 1
            cnt[ord(target[i]) - ord("a")] -= 1

        # Try from right to left
        t = list(target)
        for i in range(len(s) - 1, -1, -1):
            b = ord(t[i]) - ord("a")
            cnt[b] += 1  # Reversal of consumption
            # Check if the prefix can fully match
            if min(cnt) < 0:
                continue
            # Find the smallest available character larger than b.
            for j in range(b + 1, 26):
                if cnt[j] > 0:
                    cnt[j] -= 1
                    t[i] = chr(ord("a") + j)
                    return "".join(t[: i + 1]) + self.getMinString(cnt)

        return ""

    # Get the lexicographically smallest string (in ascending order)
    def getMinString(self, cnt: list[int]) -> str:
        res = []
        for i in range(26):
            res.append(chr(ord("a") + i) * cnt[i])
        return "".join(res)
```
