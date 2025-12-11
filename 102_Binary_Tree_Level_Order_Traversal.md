# C++
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        std::vector<std::vector<int>> res;
        if (root == nullptr) {
            return res;
        }
        std::deque<TreeNode*> q;
        q.push_back(root);

        while (!q.empty()) {
            std::vector<int> vals;
            int size = q.size(); // Cannot do 'q.size()' in the loop since it changes for each iteration

            for (int i = 0; i < size; i++) {
                // Pop out the left most node
                TreeNode* node = q.front();
                q.pop_front();

                // Add the val
                vals.push_back(node->val);

                // Add if any children from Left to Right
                if (node->left != nullptr) {
                    q.push_back(node->left);
                }
                if (node->right != nullptr) {
                    q.push_back(node->right);
                }
            }
            res.push_back(vals);
        }

        return res;
    }
};

```

# Python3
```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        res = []
        q = deque([root]) if root else None
        while q:
            vals = []
            for i in range(len(q)):
                node = q.popleft()
                vals.append(node.val)
                q.append(node.left) if node.left else None
                q.append(node.right) if node.right else None
            res.append(vals)
        return res
```

# Time & Space
```
- N = Number of nodes
- Time = O(N) because we will traverse all N nodes
- Space = O(N) because if it is a Perfect Binary Tree, there are N/2 leaves
```

# Notes
- `deque` is the best data-structure to add and delete elements at the edges
- Very useful for BST problems
- Available in both C++ and Python3
