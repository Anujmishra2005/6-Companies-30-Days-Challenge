class Solution:
    def findHighAccessEmployees(self, access_times: List[List[str]]) -> List[str]:
        d, ans = defaultdict(list), []
        for emp, time in access_times:
            d[emp].append(60*int(time[:2])+int(time[2:]))
        for emp in d:
            d[emp].sort()
            for x, y in zip(d[emp], d[emp][2:]):
                if y - x < 60:
                    ans.append(emp)
                    break
        return list(ans)
