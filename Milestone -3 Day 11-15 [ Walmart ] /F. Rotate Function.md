class Solution:
    def maxRotateFunction(self, nums: List[int]) -> int:
        n=len(nums)
        s=sum(nums)
        temp=sum(i*nums[i] for i in range(n))
        maxi=temp
        for i in range(1,n):
            temp+=s-n*nums[n-i]
            maxi=max(maxi,temp)
        return maxi
