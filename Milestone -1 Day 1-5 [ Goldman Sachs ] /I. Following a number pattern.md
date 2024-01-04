class Solution:
    def printMinNumberForPattern(self,s):
        ans = ''
        st = ''
        n = 1
        for i in s:
            st+=str(n)
            if i=='I':
                ans += st[::-1]
                st = ''
            n+=1
        st += str(n)
        ans += st[::-1]
        return ans
