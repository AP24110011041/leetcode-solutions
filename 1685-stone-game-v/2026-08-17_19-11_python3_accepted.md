# 1685. Stone Game V
  
<br>**Problem:** https://leetcode.com/problems/stone-game-v/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Math, Dynamic Programming, Game Theory<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-17 19:11 local time

**Runtime:** 2070 ms (beats 60.389399999999796%)
**Memory:** 53.8 MB (beats 37.253799999999835%)


<!-- leetgit:submissionId=2110185341 codeHash=8bb660506a393c7e0e9b382689e6cc8b5f6c7d483ebc41c42996dd1e2f6db7b1 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def stoneGameV(self, stoneValue: List[int]) -> int:
        prefix = list(accumulate(stoneValue, initial=0))

        @cache
        def dfs(l, r):
            if l >= r:
                return 0

            ans = 0
            left_sum = 0
            right_sum = prefix[r + 1] - prefix[l]

            for k in range(l, r):
                left_sum += stoneValue[k]
                right_sum -= stoneValue[k]

                if left_sum < right_sum:
                    # Alice keeps the left side.
                    #
                    # If ans >= 2 * left_sum, this split
                    # cannot improve the answer.
                    if ans >= 2 * left_sum:
                        continue

                    ans = max(
                        ans,
                        left_sum + dfs(l, k)
                    )

                elif left_sum > right_sum:
                    # Alice keeps the right side.
                    #
                    # As k increases, right_sum decreases.
                    # If ans >= 2 * right_sum, then every
                    # later split is also useless.
                    if ans >= 2 * right_sum:
                        break

                    ans = max(
                        ans,
                        right_sum + dfs(k + 1, r)
                    )

                else:
                    # Equal sums: Alice can choose either side.
                    ans = max(
                        ans,
                        left_sum + dfs(l, k),
                        right_sum + dfs(k + 1, r)
                    )

            return ans

        return dfs(0, len(stoneValue) - 1)
```
