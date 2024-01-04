class Solution:
    def countDistinct(self, nums: List[int], k: int, p: int) -> int:
        nums2 = [int(x % p == 0) for x in nums]
        pref_sum = list(accumulate(nums2))
        l = len(pref_sum)
        s = set()
        sol = 0
        for left, x in enumerate(pref_sum):
            if nums2[left] == 1:
                tar = x + k
            else:
                tar = x + 1 + k
            right = bisect_left(pref_sum, tar, lo=left)
            for end in range(left + 1, right + 1):
                t = tuple(nums[left:end])
                if t not in s:
                    s.add(t)
        return len(s)
