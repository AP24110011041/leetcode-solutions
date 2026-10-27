# 4342. Create Grid With Exactly One Path
  
<br>**Problem:** https://leetcode.com/problems/create-grid-with-exactly-one-path/<br>

**Difficulty:** Easy<br>
**Topics:** None<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-27 20:50 local time

**Runtime:** 6 ms (beats 11.8853%)
**Memory:** 19.2 MB (beats 62.29509999999999%)


<!-- leetgit:submissionId=2183191011 codeHash=b0f1d3758bf42f67addf2a960eb59313d144920c03801d21b1d3e25bfc65d7f1 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def createGrid(self, m: int, n: int) -> list[str]:
        res = [['#'] * n for _ in range(m)]
        r = c = 0
        
        res[r][c] = '.'
        
        while r < m - 1 or c < n - 1:
            if r < m - 1 and (c == n - 1 or abs((r + 1) * (n - 1) - c * (m - 1)) <= abs(r * (n - 1) - (c + 1) * (m - 1))):
                r += 1
            else:
                c += 1
                
            res[r][c] = '.'
            
        return [''.join(row) for row in res]
```
