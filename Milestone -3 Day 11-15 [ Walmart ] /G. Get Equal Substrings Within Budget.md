class Solution:
    def equalSubstring(self, s: str, t: str, maxCost: int) -> int:
        left = ans = curr = 0
        for i in range(len(s)):
            curr += abs(ord(s[i]) - ord(t[i]))
            while curr > maxCost:
                curr -= abs(ord(s[left]) - ord(t[left]))
                left += 1
            ans = max(ans, i - left + 1)
        return ans
