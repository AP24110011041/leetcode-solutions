# 4033. Longest Subsequence With Non-Zero Bitwise XOR
  
<br>**Problem:** https://leetcode.com/problems/longest-subsequence-with-non-zero-bitwise-xor/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Bit Manipulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-16 00:07 local time

**Runtime:** 48 ms (beats 23.386200000000017%)
**Memory:** 33.1 MB (beats 88.70960000000001%)


<!-- leetgit:submissionId=2108146763 codeHash=40797188c05ad7ebe31b705a05b0dfdddec94bac60bcd4d6d8abd18bd73266f1 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def longestSubsequence(self, nums: list[int]) -> int:
        tot = nz = 0

        for n in nums:
            nz |= n > 0
            tot ^= n

        return nz * (len(nums) - (not tot))
```
