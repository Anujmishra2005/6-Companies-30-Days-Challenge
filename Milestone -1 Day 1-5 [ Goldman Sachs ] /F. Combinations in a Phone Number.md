class Solution:
    def build_map(self,hmap):
        hmap['2'] = "abc"
        hmap['3'] = "def"
        hmap['4'] = "ghi"
        hmap['5'] = "jkl"
        hmap['6'] = "mno"
        hmap['7'] = "pqrs"
        hmap['8'] = "tuv"
        hmap['9'] = "wxyz"

    def backtrack(self,length, digits, hmap, temp, result, idx):
        if len(temp) == length:
            result.append(temp[:])
            return
        for char in hmap[digits[idx]]:
            temp += char
            self.backtrack(length, digits, hmap, temp, result, idx + 1)
            temp = temp[:-1]
    def letterCombinations(self, digits: str) -> List[str]:
        result = []
        hmap = {}
        self.build_map(hmap)
        if len(digits) == 0:
            return result
        self.backtrack(len(digits), digits, hmap, "", result, 0)
        return result
