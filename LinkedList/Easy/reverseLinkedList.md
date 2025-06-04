<h1>Question: <a href="https://leetcode.com/problems/reverse-linked-list/description/">Reverse Linked List</a></h1>

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        
        ListNode* prev = nullptr;
        ListNode* current = head;
        while (current != nullptr) {
            ListNode* next = current->next;
            current->next = prev;
            prev = current;
            current = next;
        }

        return prev;
        
    }
};
```

**Data structures/Algorithms used**: LinkedList, Two-pointers

**Time complexity**: O(n) (n = length of linkedlist starting at `head`)

**Space complexity**: O(n) (n = length of linkedlist starting at `head`)

**Time taken**: 5 mins

**Explanation:**
A two-pointer approach, with `prev` and `current` pointers used for updates during traversal.

`prev` is initialized to a `nullptr` (representing the `next` pointer of the new tail), whereas `current` is initialized to `head`. As we traverse the linked list, the `next` node of the `current` node is stored in a temporary variable: `next`. Then the `current->next` node is updated to be the `prev` node (the node behind the `current`). 

The `prev` node is then set to the `current` node and the `current` node is set to `next` that stored the original next node. This is a way to "increment" both pointers.

Finally, at the end of the traversal, the `prev` pointer will point to the head of the reverse linked list (which was the tail of the original linked list). So, this `prev` is returned.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>head = [1,2,3,4,5] </code>  | [5,4,3,2,1] |
| <code>head = [1,2] </code>  | [2, 1] |
| <code>head = [] </code>  | [] |

**Statistics:** Beats 100% of solutions in runtime and 70.40% of solutions in memory usage

![image](https://github.com/user-attachments/assets/36a3c5c0-06ff-4e05-8f9a-68904df0e03a)



