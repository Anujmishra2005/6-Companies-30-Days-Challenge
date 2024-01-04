class Solution:
    def smallestTrimmedNumbers(self, nums: List[str], queries: List[List[int]]) -> List[int]:
        
        trim_cache = {}
        result_cache = {}
        
        output = []
        
        def quickselect(lst, l, r, k):
            if l == r:
                return lst[k - 1]
            pi = partition(lst, l, r)
            if k - 1 < pi:
                return quickselect(lst, l, pi - 1, k)
            elif k - 1 > pi:
                return quickselect(lst, pi + 1, r, k)
            else:
                return lst[k - 1]
        
        def partition(lst, l, r):
            p = randint(l, r)
            lst[p], lst[r] = lst[r], lst[p]
            i = l
            for j in range(l, r):
                if lst[j][0] < lst[r][0] or (lst[j][0] == lst[r][0] and lst[j][1] < lst[r][1]):
                    lst[j], lst[i] = lst[i], lst[j]
                    i += 1
            lst[r], lst[i] = lst[i], lst[r]
            return i
        
        for k, trim in queries:
            if trim not in trim_cache:
                trim_cache[trim] = [(int(nums[i][-trim:]), i) for i in range(len(nums))]
            if (k, trim) not in result_cache:
                result_cache[(k, trim)] =  quickselect(trim_cache[trim], 0, len(nums) - 1, k)[1]
            output.append(result_cache[(k, trim)])
        
        return output
