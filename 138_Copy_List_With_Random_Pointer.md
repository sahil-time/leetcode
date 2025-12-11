# C
```c
struct Node* copyRandomList(struct Node* head) {
    if (head == NULL) {
        return NULL;
    }

    // In-Place modify the linked list [ Add the new node after each original node ]
    struct Node* cur = head;
    while (cur != NULL) {
        struct Node* next = cur->next;
        cur->next = (struct Node*)malloc(sizeof(struct Node));
        cur->next->val = cur->val;
        cur->next->next = next;
        cur = next;
    }

    // Connect Random Pointers
    cur = head;
    while (cur != NULL) {
        if (cur->random != NULL) {
            cur->next->random = cur->random->next;
        } else {
            cur->next->random = NULL;
        }
        cur = cur->next->next;
    }

    // Extract the new list
    cur = head;
    struct Node* res = cur->next;
    while (cur != NULL) {
        struct Node* next = cur->next->next;
        if (next != NULL) {
            cur->next->next = next->next;
            cur->next = next;
        }
        cur = next;
    }
    return res;
}
```

# C++
```cpp
class Solution {
private:

public:
    Node* copyRandomList(Node* head) {

    }
};
```

# Python3
```python
class Solution:
    def _copyRandomList1(self, head):
        if not head:
            return None

        # In-place modify the linked list by adding new nodes after each original node
        cur = head
        while cur:
            next = cur.next
            cur.next = Node(cur.val)
            cur.next.next = next
            cur = next

        # Connect the random pointers of the new list
        cur = head
        while cur:
            cur.next.random = cur.random.next if cur.random else None
            cur = cur.next.next

        # Extract the new LL and return its head
        cur = head
        res = cur.next
        while cur:
            next = cur.next.next
            cur.next.next = next.next if next else None
            cur.next = next
            cur = next

        return res

    def _copyRandomList2(self, head):
        old_new_map = {None: None}
        cur = head
        while cur:
            old_new_map[cur] = Node(cur.val)
            cur = cur.next
        cur = head
        while cur:
            old_new_map[cur].next = old_new_map[cur.next]
            old_new_map[cur].random = old_new_map[cur.random]
            cur = cur.next
        return old_new_map[head]

    def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        # return self._copyRandomList1(head) # O(N) Time & O(1) Extra space
        return self._copyRandomList2(head) # O(N) Time & O(N) Extra space
```

# Time & Space
```
- N = Number of nodes in LL
- Time = O(2N) or O(3N) ~ O(N)
- Space = O(N) for 2nd solution and O(1) for the 1st solution
```
