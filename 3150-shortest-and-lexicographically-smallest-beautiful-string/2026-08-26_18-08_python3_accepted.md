# 3150. Shortest and Lexicographically Smallest Beautiful String
  
<br>**Problem:** https://leetcode.com/problems/shortest-and-lexicographically-smallest-beautiful-string/<br>

**Difficulty:** Medium<br>
**Topics:** String, Sliding Window<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-26 18:08 local time

**Runtime:** 1 ms (beats 61.7117%)
**Memory:** 19.3 MB (beats 30.630599999999987%)


<!-- leetgit:submissionId=2120789506 codeHash=293f97f0ac5a66f2fdc5b7a27c779f1cc194eb0180eaa5eb2dbb594c12da8641 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def shortestBeautifulSubstring(self, s: str, k: int) -> str:
        answer = ""
        left = 0
        ones = 0

        for right in range(len(s)):
            if s[right] == '1':
                ones += 1

            while ones > k:
                if s[left] == '1':
                    ones -= 1
                left += 1

            while ones == k and s[left] == '0':
                left += 1

            if ones == k:
                candidate = s[left:right + 1]

                if (
                    not answer
                    or len(candidate) < len(answer)
                    or (len(candidate) == len(answer) and candidate < answer)
                ):
                    answer = candidate

        return answer
```
