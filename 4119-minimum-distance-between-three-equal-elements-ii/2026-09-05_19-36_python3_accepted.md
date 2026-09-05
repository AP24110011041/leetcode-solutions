# 4119. Minimum Distance Between Three Equal Elements II
  
<br>**Problem:** https://leetcode.com/problems/minimum-distance-between-three-equal-elements-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-05 19:36 local time

**Runtime:** 310 ms (beats 75.5378999999999%)
**Memory:** 50.6 MB (beats 51.977599999999924%)


<!-- leetgit:submissionId=2131786564 codeHash=8083f69b3ba43e21b7c3ff81a56c1ec79cf8504c547c13b19646b1e454df0a34 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
from collections import defaultdict

class Solution:
    def minimumDistance(self, nums):
        mp = defaultdict(list)

        for i, num in enumerate(nums):
            mp[num].append(i)

        mini = float('inf')

        for temp in mp.values():
            m = len(temp)

            if m >= 3:
                for i in range(m - 2):
                    a = temp[i]
                    b = temp[i + 1]
                    c = temp[i + 2]

                    diff = 2 * (c - a)
                    mini = min(mini, diff)

        return -1 if mini == float('inf') else mini
```
