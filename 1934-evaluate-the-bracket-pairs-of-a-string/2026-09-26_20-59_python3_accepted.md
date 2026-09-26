# 1934. Evaluate the Bracket Pairs of a String
  
<br>**Problem:** https://leetcode.com/problems/evaluate-the-bracket-pairs-of-a-string/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, String<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-26 20:59 local time

**Runtime:** 35 ms (beats 95.01550000000002%)
**Memory:** 51.9 MB (beats 28.971899999999998%)


<!-- leetgit:submissionId=2154074736 codeHash=2f9005098973bee303dac4d92ae238fb1b74639e2b24a23a137c4bfb2938e925 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def evaluate(self, s: str, K: List[List[str]]) -> str:
        d = dict(K)
        res, i = [], 0

        while i < len(s):
            if s[i] == '(':
                j = s.find(')', i + 1)
                res.append(d.get(s[i + 1:j], '?'))
                i = j
            else:
                res.append(s[i])
            i += 1

        return "".join(res)
```
