# C
```c
int calcArea(const int* height, int l, int r) {
    int min = height[l] > height[r] ? height[r] : height[l];
    return min * (r - l);
}
int maxArea(int* height, int heightSize) {
    int l = 0;
    int r = heightSize - 1;
    int max_area = calcArea(height, l, r);
    while (l < r) {
        if (height[l] < height[r]) {
            l += 1;
        } else {
            r -= 1;
        }
        int cur_area = calcArea(height, l, r);
        max_area = max_area > cur_area ? max_area : cur_area;
    }
    return max_area;
}
```

# C++
```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int l = 0;
        int r = height.size() - 1;
        int max_area = std::min(height[l], height[r]) * (r - l);
        while (l < r) {
            if (height[l] < height[r]) {
                l += 1;
            } else {
                r -= 1;
            }
            int cur_area = std::min(height[l], height[r]) * (r - l);
            max_area = std::max(max_area, cur_area);
        }
        return max_area;
    }
};
```

# Python3
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r = 0, len(height) - 1
        max_area = min(height[l], height[r]) * (r - l)
        while l < r:
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
            cur_area = min(height[l], height[r]) * (r - l)
            max_area = max(max_area, cur_area)
        return max_area
```

# Time & Space
```
- N = len(height)
- Time = O(N)
- Space = O(1)
```

# Notes
- This algo uses a Greedy approach
- Key Insight: Always move the pointer with the smaller height
- This is because the area is limited by the smaller height, so always move that
