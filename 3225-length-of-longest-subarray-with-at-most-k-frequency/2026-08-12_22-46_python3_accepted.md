# 3225. Length of Longest Subarray With at Most K Frequency
  
<br>**Problem:** https://leetcode.com/problems/length-of-longest-subarray-with-at-most-k-frequency/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, Sliding Window<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-12 22:46 local time

**Runtime:** 253 ms (beats 60.27959999999992%)
**Memory:** 34.9 MB (beats 99.8004%)


<!-- leetgit:submissionId=2104523984 codeHash=4336edcf45904231a4918cd2e62e3d592c787e7cbad65f00e960071c6a7ce88c notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxSubarrayLength(self, nums: List[int], k: int) -> int:
        n, cnt=len(nums), 0
        freq=defaultdict(int)
        l=0
        for r, x in enumerate(nums):
            freq[x]+=1
            while freq[x]>k:
                freq[nums[l]]-=1
                l+=1
            cnt=max(cnt, r-l+1)
        return cnt
```
