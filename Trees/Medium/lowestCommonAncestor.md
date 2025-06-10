<h1>Question: <a href="https://leetcode.com/problems/validate-binary-search-tree/description/">Validate BST</a></h1>

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (!root) return nullptr;
        if (p->val < root->val && q->val < root->val) {
            return lowestCommonAncestor(root->left, p, q);
        } else if (p->val > root->val && q->val > root->val) {
            return lowestCommonAncestor(root->right, p, q);
        }

        return root;
    }
};
```

**Data structures/Algorithms used**: Binary search tree

**Time complexity**: O(h) (h = height of tree)

**Space complexity**: O(h) (h = height of tree)

**Time taken**: 10 mins

**Explanation:**
A recursive approach broken down into three cases. We are guaranteed that the argument tree is a BST, hence we can leverage the BST property.

1) The base case: if the node of the current recursive call stack doesn't exist (i.e we have reached beyond a leaf), return a `nullptr`.
2) If the `p`, `q` nodes' values are less than the current node's (`root`) value, this means they are both located in the left subtree and have a lower common ancestor.
3) If the `p`, `q` nodes' values are greater than the current node's value, this means they are both located in the right subtree and have a lower common ancestor.

In all other cases, such as one of `p` and `q` nodes' values being greater and the other smaller than the current node's value this means they are on opposite subtrees and we have already found our lowest common ancestor. If either of the nodes' values is equal to the current node, as per the assumption that a node is a descendant of itself (i.e `p` is it's own ancestor), we have already found our lowest common ancestor.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8</code>  | 6 |
| <code>root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4</code>  | 2 |
| <code>root = [2,1], p = 2, q = 1</code>  | 2 |



**Statistics:** Beats 54.95% of solutions in runtime and 99.05% of solutions in memory usage

