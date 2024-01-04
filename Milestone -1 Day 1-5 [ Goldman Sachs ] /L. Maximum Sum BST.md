class Solution:
    def maxSumBST(self, root: TreeNode) -> int:
        if not root:
            return 0
        self.s = 0
        def helper(cur):
            a, amin, amax = helper(cur.left) if cur.left else (0, float('inf'), float('-inf'))
            b, bmin, bmax = helper(cur.right) if cur.right else (0, float('inf'), float('-inf'))
            if a is not None and b is not None:
                if cur.val > amax and cur.val < bmin:
                    s = cur.val + a + b
                    self.s = max(self.s, s)
                    return s, min(cur.val, amin), max(cur.val, bmax)
            return (None, None, None)
        helper(root)
        return self.s
