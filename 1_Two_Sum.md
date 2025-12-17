# C
```c
struct hashTable {
    int key;
    int val;
    UT_hash_handle hh;
};

int* twoSum (int* nums, int numSize, int target, int* returnSize) {
    struct hashTable* hmap = NULL;
    struct hashTable* entry = NULL;
    int* result = (int*)malloc(2 * sizeof(int));

    for (int i = 0; i < numSize; i++) {

        // Check if 'complement' exists in the Hash-Table
        int complement = target - nums[i];
        HASH_FIND_INT(hmap, &complement, entry);
        if (entry != NULL) {
            result[0] = entry->val;
            result[1] = i;
            *returnSize = 2;
            HASH_CLEAR(hh, hmap);
            return result;
        }

        // Add the key-value in the Hash-Table
        entry = (struct hashTable*)malloc(sizeof(struct hashTable));
        entry->key = nums[i];
        entry->val = i;
        HASH_ADD_INT(hmap, key, entry);
    }

    // Could not find the 2 sum, so clear the Hash-Table and return 0
    HASH_CLEAR(hh, hmap);
    *returnSize = 0;
    return result;
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
