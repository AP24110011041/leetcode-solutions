# 3975. XOR After Range Multiplication Queries II
  
<br>**Problem:** https://leetcode.com/problems/xor-after-range-multiplication-queries-ii/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Divide and Conquer, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-05 19:35 local time

**Runtime:** 6310 ms (beats 28.936000000000437%)
**Memory:** 68.6 MB (beats 94.92390000000002%)


<!-- leetgit:submissionId=2131785362 codeHash=1222b1c425c4b69fa02d8396375136f461fbf92cef0a564924881155843c2034 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def xorAfterQueries(self, nums: List[int], queries: List[List[int]]) -> int:
        n = len(nums)
        MOD = 10**9 + 7
        limit = math.isqrt(n)
        
        # Group queries with small k for later processing
        lightK = defaultdict(list)
        
        for q in queries:
            l, r, k, v = q
            
            if k >= limit:
                # Large k: apply brute force
                for i in range(l, r + 1, k):
                    nums[i] = (nums[i] * v) % MOD
            else:
                # Small k: process later
                lightK[k].append(q)
                
        for k, query_list in lightK.items():
            # Process small queries grouped by step size k
            diff = [1] * n
            
            for q in query_list:
                l, r, _, v = q
                
                # Multiply starting position
                diff[l] = (diff[l] * v) % MOD
                
                # Cancel the multiplication using modular inverse
                steps = (r - l) // k
                nxt = l + (steps + 1) * k
                if nxt < n:
                    # pow(v, -1, MOD) computes the modular inverse natively
                    diff[nxt] = (diff[nxt] * pow(v, -1, MOD)) % MOD
                    
            # Propagate the multipliers with a step size of k
            for i in range(n):
                if i >= k:
                    diff[i] = (diff[i] * diff[i - k]) % MOD
                nums[i] = (nums[i] * diff[i]) % MOD
                
        ans = 0
        for num in nums:
            ans ^= num
            
        return ans
```
