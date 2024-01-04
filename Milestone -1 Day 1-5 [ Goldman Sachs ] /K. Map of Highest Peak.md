class Solution:
    def highestPeak(self, x: List[List[int]]) -> List[List[int]]:
        m,n=len(x),len(x[0])
        q=[]
        for i in range(m):  
            for j in range(n):
                if x[i][j]==1:
                    x[i][j]=0
                    q.append((i,j))
                else:
                    x[i][j]=-1
        while q:
            i,j=q.pop(0)
            for d,e in ((i+1,j),(i,j+1),(i-1,j),(i,j-1)):
                if 0<=d<m and 0<=e<n and x[d][e]==-1:
                    x[d][e]=x[i][j]+1
                    q.append((d,e))
        return x
