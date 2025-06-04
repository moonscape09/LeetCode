<h1>Question: <a href="https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/description">Maximum Twin Sum of a Linked List</a></h1>

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
    int pairSum(ListNode* head) {
        ListNode* curr = head;

        ListNode *slow = head, *fast = head;

        int mid = 0;
        vector <int> leftHalf;
        vector<int> rightHalf;
        while (fast && fast->next) {
            leftHalf.push_back(slow->val);
            slow = slow->next;
            mid ++;
            fast = fast->next->next;
        }
        while (slow != nullptr) {
            rightHalf.push_back(slow->val);
            slow = slow->next;
        }
    
        int maxSum = 0;
        for (int i = 0; i < mid; i++) {
            int sum = leftHalf[i] + rightHalf[mid - 1 - i];
            if (sum > maxSum) {
                maxSum = sum;
            }
        }
        
        return maxSum;

    }

};
```

**Data structures/Algorithms used**: LinkedList, Slow/Fast pointers

**Time complexity**: O(n) (n = length of linkedlist starting at `head`)

**Space complexity**: O(n) (n = length of linkedlist starting at `head`)

**Time taken**: 15 mins

**Explanation:**
Slow/fast pointers are used to locate the middle node. An integer `mid` is also incremented to equal to half the length of the linked list.

The left and right halves of the linked list are stored in the arrays: `leftHalf` and `rightHalf`, respectively. 

Finally, both arrays are simultaneously iterated, and given the nature of symmetry, `leftHalf` iterates from the start and `rightHalf` iterates from the end. The iterations go on until `mid` (set previously) is reached. The corresponding, symmetrical values are added, and if their sum is greater than `maxSum`, then `maxSum` is updated.

Finally, `maxSum` is returned.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>head = [5,4,2,1] </code>  | 6 |
| <code>head = [4,2,2,3] </code>  | 7 |
| <code>head = [1,100000] </code>  | 100001 |

**Statistics:** Beats 100% of solutions in runtime and 6.02% of solutions in memory usage

![image](https://github.com/user-attachments/assets/9556bb13-1bcc-4887-b507-a62f46a0377b)


