# 3742. Maximum Number of Items From Sale I
  
<br>**Problem:** https://leetcode.com/problems/maximum-number-of-items-from-sale-i/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Dynamic Programming, Greedy<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-27 08:31 local time

**Runtime:** 734 ms (beats 90.19599999999997%)
**Memory:** 19.7 MB (beats 57.84299999999999%)


<!-- leetgit:submissionId=2204271118 codeHash=c6f97f5da57d62ab687df41ff200bf6388afc7832c9ef360f27563bfe1fb152f notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maximumSaleItems(self, items: List[List[int]], budget: int) -> int:
        factors, prices = zip(*items)
        have = [0] * (max(factors) + 1)  # have[f]: items with factor f
        for factor in factors:
            have[factor] += 1
        gains = {factor: sum(have[factor::factor]) for factor in set(factors)}  # every factor-th cell is a multiple

        cheapest = min(prices)
        best = [money // cheapest for money in range(budget + 1)]  # no first copies yet: everything goes to the cheapest item
        for factor, price in items:
            if (gain := gains[factor]) > price // cheapest:  # else the same money buys as many copies of the cheapest item
                for money in range(budget, price - 1, -1):  # backwards: one first copy per item
                    best[money] = max(best[money], best[money - price] + gain)
        return best[budget]
```
