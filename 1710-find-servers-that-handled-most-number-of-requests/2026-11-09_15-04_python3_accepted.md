# 1710. Find Servers That Handled Most Number of Requests
  
<br>**Problem:** https://leetcode.com/problems/find-servers-that-handled-most-number-of-requests/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Heap (Priority Queue), Simulation, Ordered Set<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-09 15:04 local time

**Runtime:** 253 ms (beats 90.5408%)
**Memory:** 46 MB (beats 37.83819999999999%)


<!-- leetgit:submissionId=2192386873 codeHash=075ff835d28a392cdbea40bb4f397828a4aad11fcf6851f9959b3af8f3a5ff67 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def busiestServers(self, k: int, arrival: List[int], load: List[int]) -> List[int]:
        busy = [] # min-heap
        free = list(range(k)) # min-heap 
        freq = [0]*k
        
        for i, (ta, tl) in enumerate(zip(arrival, load)): 
            while busy and busy[0][0] <= ta: 
                _, ii = heappop(busy)
                heappush(free, i + (ii - i) % k) # circularly relocate it
            if free: 
                ii = heappop(free) % k 
                freq[ii] += 1
                heappush(busy, (ta+tl, ii))
        
        mx = max(freq)
        return [i for i, x in enumerate(freq) if x == mx]
```
