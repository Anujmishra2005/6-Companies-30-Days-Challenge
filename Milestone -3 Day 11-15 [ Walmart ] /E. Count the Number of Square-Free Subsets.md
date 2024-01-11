class Solution:
    def squareFreeSubsets(self, nums: List[int]) -> int:
        modulo = 1000000007
        primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
        # map from number to factor
        n2f = {}
        for n in range(1, 31):
            if n % 4 == 0 or n % 9 == 0 or n % 25 == 0: continue
            factor = 0
            for i, p in enumerate(primes):
                if n % p == 0:
                    # prime factorization using bitmask
                    factor += (1 << i)
            n2f[n] = factor

        # map from number to its count
        n2c = {}
        for num in nums:
            if num in n2f:
                n2c[num] = n2c.get(num, 0) + 1
            
        # some subset can have multiple ones, so speacially handle it
        one_count = n2c.get(1, 0)
        if 1 in n2c:
            del n2c[1]

        ret = 0
        # iterate over all possible number subsets
        for i in range(1, len(n2c.keys()) + 1):
            for x in combinations(n2c, i):

                # check square-free-ness
                factor_total = 0
                cont_flag = False
                for n in x:
                    if factor_total & n2f[n]:
                        cont_flag = True
                        break
                    factor_total |= n2f[n]
                if cont_flag: continue
                
                tmp = 1
                for n in x:
                    tmp = (tmp * n2c[n]) % modulo
                ret = (ret + tmp) % modulo
                    
        return ((ret + 1) * (2 ** one_count) - 1) % modulo
