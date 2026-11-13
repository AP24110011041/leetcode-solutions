# 3674. Count Non-Decreasing Subarrays After K Operations
  
<br>**Problem:** https://leetcode.com/problems/count-non-decreasing-subarrays-after-k-operations/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Stack, Segment Tree, Queue, Sliding Window, Monotonic Stack, Monotonic Queue<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-14 00:39 local time

**Runtime:** 304 ms (beats 76.92310000000002%)
**Memory:** 36.7 MB (beats 89.7436%)


<!-- leetgit:submissionId=2195520568 codeHash=2e69b8ea781e3206eb904f87f61cfe315225f867e0a73d8282c3d38e544af276 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def countNonDecreasingSubarrays(self, A: List[int], k: int) -> int:
        A = A[::-1]
        res = 0
        q = deque()
        i = 0
        for j in range(len(A)):
            while q and A[q[-1]] < A[j]:
                r = q.pop()
                l = q[-1] if q else i - 1
                k -= (r - l) * (A[j] - A[r])
            q.append(j)
            while k < 0:
                k += A[q[0]] - A[i]
                if q[0] == i:
                    q.popleft()
                i += 1
            res += j - i + 1
        return res
        
```
