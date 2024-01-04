class Solution:

    def __init__(self, m: int, n: int):
        self.mn = m * n
        self.n = n
        self.flipped = set()

    def flip(self) -> List[int]:
        iflat = randrange(0, self.mn)
        while iflat in self.flipped:
            iflat = randrange(0, self.mn)
        self.flipped.add(iflat)
        return [iflat // self.n, iflat % self.n]

    def reset(self) -> None:
        self.flipped = set()


# Your Solution object will be instantiated and called as such:
# obj = Solution(m, n)
# param_1 = obj.flip()
# obj.reset()
