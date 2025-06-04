<h1>Question: <a href="https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/">Delete Middle Node of a Linked List</a></h1>

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
    ListNode* deleteMiddle(ListNode* head) {
        ListNode* curr = head;
        
        int n = 0;
        while (curr != nullptr) {
            curr = curr->next;
            n ++;
        }
        if (n == 1) return nullptr; // base case: if only one node in the linked list, then it just becomes empty
        n = n / 2;
        curr = head;
        while (n - 1 != 0) {
            curr = curr->next;
            n --;
        }
        curr->next = curr->next->next;
        return head;
    }
};
```

**Data structures/Algorithms used**: LinkedList

**Time complexity**: O(n) (n = length of linkedlist starting at `head`)

**Space complexity**: O(1) (n = length of linkedlist starting at `head`)

**Time taken**: 10 mins

**Explanation:**
A multi-pass approach, where the first traversal simply counts the number of nodes, `n`, in the linked list.

The `n` is then set to the floor of it's half (`n / 2`), to mark the index of the middle node in the linked list. The linked list is traversed again up till the node before this index (by decrementing `n` every node).

Now that we have gotten the previous node of the middle node (the one we want to delete), we simply set the `next` pointer of the previous node to the `next` pointer of the middle node. Since we weren't asked to free the deleted node from memory, we didn't use temporary variables and the `delete` keyword for deallocation.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>head = [1,3,4,7,1,2,6] </code>  | [1,3,4,1,2,6] |
| <code>head = [1,2,3,4] </code>  | [1,2,4] |
| <code>head = [2, 1] </code>  | [2] |

**Statistics:** Beats 100% of solutions in runtime and 83.85% of solutions in memory usage

