class Solution:
    def minimizeSet(self, D1: int, D2: int, C1: int, C2: int) -> int:
        return bisect_left(range(10**10), True, key=lambda M: M-M//D1 >= C1 and 
                                                              M-M//D2 >= C2 and 
                                                              M-M//lcm(D1,D2) >= C1+C2) 
