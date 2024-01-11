from collections import deque, defaultdict

class Solution:
    def amountOfTime(self, root, start):
        map = defaultdict(set)
        self.convert(root, 0, map)
        q = deque()
        q.append(start)
        minute = 0
        visited = set()
        visited.add(start)

        while q:
            level_size = len(q)
            while level_size > 0:
                current = q.popleft()

                for num in map[current]:
                    if num not in visited:
                        visited.add(num)
                        q.append(num)
                level_size -= 1
            minute += 1
        return minute - 1

    def convert(self, current, parent, map):
        if not current:
            return
        if current.val not in map:
            map[current.val] = set()
        adjacent_list = map[current.val]
        if parent != 0:
            adjacent_list.add(parent)
        if current.left:
            adjacent_list.add(current.left.val)
        if current.right:
            adjacent_list.add(current.right.val)
        self.convert(current.left, current.val, map)
        self.convert(current.right, current.val, map)
