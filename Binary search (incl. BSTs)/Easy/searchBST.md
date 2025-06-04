<h1>Question: <a href="https://leetcode.com/problems/search-in-a-binary-search-tree/description">Maximum Search BST</a></h1>

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) {
        
        TreeNode* curr = root;
        while (curr != nullptr) {
            if (val < curr->val) {
                curr = curr->left;
            } else if (val > curr->val) {
                curr = curr->right;
            } else {
                return curr;
            }
        }

        return NULL;
        
    }
};
```

**Data structures/Algorithms used**: Binary search tree

**Time complexity**: Balanced tree: O(log n), Skewed tree: O(n) (n = number of nodes in BST)

**Space complexity**: O(1)

**Time taken**: 3 mins

**Explanation:**
The tree is traversed with a `curr` pointer. If the target `val` is smaller than the `curr` node's `val`, then `curr` is set to the left subtree's root. If the target `val` is larger, then the `curr` is set to the right subtree's root. These conditions are based on the BST property (smaller values in left subtree for every node and larger values on right subtree). 

If the target `val` is found, that is if the `curr` node's value is equal to `val`, then the `curr` node is returned.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [4,2,7,1,3] val = 2</code>  | [2, 1, 3] |
| <code>root = [4,2,7,1,3] val = 5</code>  | [] |

**Statistics:** Beats 100% of solutions in runtime and 61.19% of solutions in memory usage

![image](https://github.com/user-attachments/assets/03ba013e-e4a6-473b-9dc1-47bbca16d096)
