class Solution:
    def frequencySort(self, s: str) -> str:
        dct = {i : s.count(i) for i in set(s)}
        dct = sorted(dct.items(),key=lambda x:x[1], reverse=True)
        return ''.join([k*v for k,v in dct])
