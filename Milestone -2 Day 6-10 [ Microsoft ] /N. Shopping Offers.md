class Solution:
    def helper(self,price,special,needs,memo):
        key = tuple(needs)
        if key in memo:
            return memo[key]
        ans = 0
        for i in range(len(needs)):
            ans += price[i]*needs[i]
        for offer in special:
            valid = True
            for i in range(len(needs)):
                if offer[i] > needs[i]:
                    valid = False
                    break
            if valid:
                new = needs[:]
                offerprice = offer[-1]
                for i in range(len(needs)):
                    new[i]-= offer[i]
                newprice = offerprice+self.helper(price,special,new,memo)
                ans = min(ans,newprice)
        memo[key] = ans
        return memo[key]                     
    def shoppingOffers(self, price: List[int], special: List[List[int]], needs: List[int]) -> int:
        return self.helper(price,special,needs,dict()) 
