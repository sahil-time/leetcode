# C
```c
struct hashTable {
    int key;
    int value;
    UT_hash_handle hh;
};

int* two_sum (int* nums, int numSize, int target, int* returnSize) {
    returnSize = (int*)malloc(2 * sizeof(int));
    for (int i = 0; i < numSize; i++) {

    }
}
```

# C++
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::unordered_map<int, int> hmap;
        std::vector<int> res(2);
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            if (hmap.contains(complement)) {
                res[0] = hmap[complement];
                res[1] = i;
                return res; // Return Value Optimization [ Zero Copy ]
            }
            hmap[nums[i]] = i;
        }
        return res;
    }
};
```

# Python3
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hmap = collections.defaultdict(int)
        for i, num in enumerate(nums):
            complement = target - num
            if complement in hmap:
                return [hmap[complement], i]
            hmap[num] = i
```

# Time & Space
```
- N = Length of the array
- Time = O(N)
- Space = O(N)
```
