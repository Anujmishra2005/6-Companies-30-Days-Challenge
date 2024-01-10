class Solution:
    def minimumCost(self, source: str, target: str, original: list, changed: list, cost: list) -> int:
        inf = 10 ** 18
        c = [[inf] * 26 for _ in range(26)]
        m = len(original)

        for i in range(26):
            c[i][i] = 0

        for i in range(m):
            c[ord(original[i]) - ord('a')][ord(changed[i]) - ord('a')] = min(c[ord(original[i]) - ord('a')][ord(changed[i]) - ord('a')], cost[i])

        for k in range(26):
            for i in range(26):
                for j in range(26):
                    c[i][j] = min(c[i][j], c[i][k] + c[k][j])

        ans = 0
        n = len(source)

        for i in range(n):
            ans += c[ord(source[i]) - ord('a')][ord(target[i]) - ord('a')]
            if ans >= inf:
                return -1

        return ans
