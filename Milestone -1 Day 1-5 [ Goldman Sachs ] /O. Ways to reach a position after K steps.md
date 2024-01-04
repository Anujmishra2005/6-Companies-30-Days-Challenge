class Solution:
    def numberOfWays(self, startPos: int, endPos: int, k: int) -> int:
        d = endPos - startPos
        if k < d:
            return 0
        if (k - d) % 2 != 0:
            return 0
        col = (d + k) // 2
        return (factorial(k) // (factorial(col) * factorial(k - col))) % 1_000_000_007
