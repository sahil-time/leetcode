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
