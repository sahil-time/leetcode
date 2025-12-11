# C
```c
struct TreeNode* lowestCommonAncestorHelper(struct TreeNode* node, struct TreeNode* p, struct TreeNode* q) {
    if (node == NULL) {
        return NULL;
    }
    if (node == p || node == q) {
        return node;
    }

    struct TreeNode* left = lowestCommonAncestorHelper(node->left, p, q);
    struct TreeNode* right = lowestCommonAncestorHelper(node->right, p, q);

    if (left != NULL && right != NULL) {
        return node;
    }
    if (left != NULL) {
        return left;
    }
    if (right != NULL) {
        return right;
    }
    return NULL;
}

struct TreeNode* lowestCommonAncestor(struct TreeNode* root, struct TreeNode* p, struct TreeNode* q) {
        return lowestCommonAncestorHelper(root, p, q);
}
```

# C++
```cpp
class Solution {
private:
    TreeNode* lowestCommonAncestorHelper(TreeNode* node, TreeNode* p, TreeNode* q) {
        if (node == nullptr) {
            return nullptr;
        }
        if (node == p || node == q) {
            return node;
        }

        TreeNode* left = lowestCommonAncestorHelper(node->left, p, q);
        TreeNode* right = lowestCommonAncestorHelper(node->right, p, q);

        if (left != nullptr && right != nullptr) {
            return node;
        }
        if (left != nullptr) {
            return left;
        }
        if (right != nullptr) {
            return right;
        }
        return nullptr;
    }

public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        return lowestCommonAncestorHelper(root, p, q);
    }
};
```

# Python3
```python
class Solution:
    def _lowestCommonAncestorHelper(self, node, p, q):
        if not node:
            return None
        if node == p or node == q:
            return node

        l = self._lowestCommonAncestorHelper(node.left, p, q)
        r = self._lowestCommonAncestorHelper(node.right, p, q)

        if l and r:
            return node
        if l:
            return l
        if r:
            return r
        return None

    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        return self._lowestCommonAncestorHelper(root, p, q)
```

# Time & Space
```
- N = Number of nodes in the tree
- Time = O(N) since might traverse ALL the nodes
- Space = O(N) since we can have N stackframes
```
