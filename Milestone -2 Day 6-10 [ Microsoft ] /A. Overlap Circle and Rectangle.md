class Solution:
    def checkOverlap(self, radius: int, x_center: int, y_center: int, x1: int, y1: int, x2: int, y2: int) -> bool:
        c1 = (x2 + x1) / 2
        c2 = (y2 + y1) / 2
        v1 = abs(x_center - c1) 
        v2 = abs(y_center - c2)
        h1 = (x2 - x1) / 2 
        h2 = (y2 - y1) / 2
        u1 = max(0, v1 - h1)
        u2 = max(0, v2 - h2)
        return (u1 * u1 + u2 * u2 <= radius * radius)
