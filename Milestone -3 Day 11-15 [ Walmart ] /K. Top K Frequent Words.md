class Solution(object):
    def topKFrequent(self, words, k):
        counts = Counter(words)
        counts = sorted(counts.items(), key = lambda x: (-x[1], x[0]))
        ans = [counts[i][0] for i in range(k)]
        return ans
