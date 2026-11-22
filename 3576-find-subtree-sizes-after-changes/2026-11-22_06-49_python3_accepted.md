# 3576. Find Subtree Sizes After Changes
  
<br>**Problem:** https://leetcode.com/problems/find-subtree-sizes-after-changes/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, String, Tree, Depth-First Search<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-22 06:49 local time

**Runtime:** 727 ms (beats 75.96239999999997%)
**Memory:** 130.6 MB (beats 23.07939999999992%)


<!-- leetgit:submissionId=2200882411 codeHash=c57d0e198132344ad444f35360492c1998517a98126248ef4e776738a83c8ce6 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def findSubtreeSizes(self, parent: List[int], s: str) -> List[int]:

        def dfs(i: int)-> None:

            ch = s[i]

            if ch in ancestor: prev = ancestor[ch]
            else: prev = None

            ancestor[ch] = i

            for node in graph[i]:
                dfs(node)
                ans[parent[node]]+= ans[node]

            ancestor[ch] = prev
            if prev is None: return
            parent[i] = prev

            return 


        ans = [1] * len(s)
        graph, ancestor = defaultdict(list), defaultdict(int)
        
        for node, par in enumerate(parent):
            graph[par].append(node)
        
        dfs(0)

        return ans
```
