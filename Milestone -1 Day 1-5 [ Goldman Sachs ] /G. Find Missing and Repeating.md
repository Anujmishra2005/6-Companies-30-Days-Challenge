#User function Template for python3

class Solution:
    def findTwoElement( self,arr, n): 
        # code here
        arr.sort()
        dic = {}
        res = []
        es = 0
        s = 0
        for i in range(0, len(arr)):
            dic[arr[i]] = dic.get(arr[i], 0)+1
        for i in dic:
            if dic[i] == 2:
                res.append(i)
                break
    
        n = len(set(arr)) + 1
        s = sum(set(arr))
        es = n * (n+1)//2
        mis = es - s
        res.append(mis)
        return res
