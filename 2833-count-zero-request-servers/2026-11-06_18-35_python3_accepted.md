# 2833. Count Zero Request Servers
  
<br>**Problem:** https://leetcode.com/problems/count-zero-request-servers/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, Sliding Window, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-06 18:35 local time

**Runtime:** 234 ms (beats 12.726400000000023%)
**Memory:** 74.1 MB (beats 11.817500000000006%)


<!-- leetgit:submissionId=2190701440 codeHash=145edd1c169a644053dae09084a36f01afa7ba8628b7ff05da48e2b5c8861ec2 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def countServers(self, n: int, logs: List[List[int]], x: int, queries: List[int]) -> List[int]:
        dico={i:0 for i in range (1,n+1)}
        logs=sorted(logs,key=lambda x:x[1])
        queries=sorted([query,i] for i,query in enumerate(queries))
        p=len(logs)
        right,left=0,-1
        countNull=n
        res=[0]*len(queries)
        for query,i in queries:
            while right <p and logs[right][1]<=query:
                serv=logs[right][0]
                if dico[serv]==0:
                    countNull-=1
                dico[serv]+=1
                right+=1
            while left+1<p and logs[left+1][1]<query-x:
                left+=1
                serv=logs[left][0]
                dico[serv]-=1
                if dico[serv]==0:
                    countNull+=1
            res[i]=countNull
        return res
            
```
