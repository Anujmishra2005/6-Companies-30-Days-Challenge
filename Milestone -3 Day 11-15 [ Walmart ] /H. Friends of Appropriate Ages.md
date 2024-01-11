class Solution:
    def numFriendRequests(self, ages: List[int]) -> int:
        cntr = Counter(ages)
        ages, pSum = [], []
        for age, cnt in sorted(cntr.items()):
            ages.append(age)
            pSum.append((pSum[-1] if len(pSum) else 0) + cnt)
        
        result = 0
        for i, age in enumerate(ages):
            if age > 14:
                result += cntr[age]*(cntr[age] - 1)
                j = bisect_right(ages, 0.5*age + 7)
                if j < i:
                    result += cntr[age]*(pSum[i-1] - (pSum[j-1] if j > 0 else 0))

        return result
