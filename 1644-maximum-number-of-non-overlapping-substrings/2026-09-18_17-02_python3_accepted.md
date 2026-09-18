# 1644. Maximum Number of Non-Overlapping Substrings
  
<br>**Problem:** https://leetcode.com/problems/maximum-number-of-non-overlapping-substrings/<br>

**Difficulty:** Hard<br>
**Topics:** Hash Table, String, Greedy, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-18 17:02 local time

**Runtime:** 41 ms (beats 99.5575%)
**Memory:** 20.2 MB (beats 88.4956%)


<!-- leetgit:submissionId=2145685916 codeHash=64c1ae22624107398ca12188e04b4c0c4779cea7487e76b7b6c3b29977b3022f notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxNumOfSubstrings(self, s: str) -> list[str]:
        counts = Counter(s)
        first = {c: s.find(c) for c in counts}
        last = {c: s.rfind(c) for c in counts}

        res = []
        queue = deque()

        for c in counts:
            queue.appendleft([first[c], last[c], counts[c]])

            left = inf
            right = -inf
            total = 0

            for x, y, z in queue:
                total += z
                left = min(left, x)
                right = max(right, y)

                if total == right - left + 1:
                    break

            if total == right - left + 1:
                res.append(s[left:right + 1])
                queue.clear()

        return res
```
