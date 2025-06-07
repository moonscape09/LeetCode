<h1>Question: <a href="https://leetcode.com/problems/invert-binary-tree/description/">Invert Binary Tree</a></h1>

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
    TreeNode* invertTree(TreeNode* root) {
        if (!root) return nullptr;

        TreeNode* temp = root->left;
        root->left = root->right;
        root->right = temp;

        invertTree(root->left);
        invertTree(root->right);

        return root;
    }
};
```

**Data structures/Algorithms used**: Binary tree

**Time complexity**: O(n) (n = number of nodes in binary tree)

**Space complexity**: O(n) (n = number of nodes in binary tree)

**Time taken**: 5 mins

**Explanation:**
A recursive algorithm that does a swap for the left and right child of the current node in the current call stack.

Base case is when the root doesn't exist, hence the recursion stops after a leaf has been reached.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [4,2,7,1,3,6,9]</code>  | [4,7,2,9,6,3,1] |
| <code>root = [2,1,3]</code>  | [2,3,1] |
| <code>root = []</code>  | [] |

**Statistics:** Beats 100% of solutions in runtime and 86.26% of solutions in memory usage
