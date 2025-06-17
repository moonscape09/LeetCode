<h1>Question: <a href="https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/">Flatten Binary Tree to Linked List</a></h1>

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
    TreeNode* recursiveFlatten(TreeNode* root) {
        if (!root->left) return root;

        TreeNode* tmp = root->right;
        root->right = recursiveFlatten(root->left);
        root->left = nullptr;

        TreeNode* curr = root;
        while (curr->right != nullptr) curr = curr->right;
        curr->right = tmp;

        return root;
    }
    void flatten(TreeNode* root) {
        if (!root) return;
        recursiveFlatten(root);
        if (root->right) flatten(root->right);
        
    }
};
```

**Data structures/Algorithms used**: Binary tree

**Time complexity**: O(n^2) (n = number of nodes in tree)

**Space complexity**: O(h)

**Time taken**: 30 mins

**Explanation:**
Uses a callback function that recursively flattens the left subtree for every left child found.

The base case of the callback is when no more left child exists. Otherwise, we store the current right child of the root in `tmp`, and reassign `root->right` to the returned flattened left subtree's root from the recursive call. We set `root->left` to null as it becomes a dangling pointer.

Afterwards, we traverse the new flattened subtree which is now on the right side of the root until no more children are found, and we place the old `root->right` subtree (stored in `tmp`) on this end. Finally, we return the root of flattened subtree.

In the original function, `flatten`, we make recursive calls on the right child in case there are any subtrees on the right side of the original `root` that have left children, and hence they must be flattened.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [1,2,5,3,4,null,6]</code>  | [1,null,2,null,3,null,4,null,5,null,6] |
| <code>root = []</code>  | [] |
| <code>root = [0]</code>  | [0] |
| <code>root = [1, null, 2, 3]</code>  | [1,null,2,null,3] |



**Statistics:** Beats 100% of solutions in runtime and 99.91% of solutions in memory usage

![image](https://github.com/user-attachments/assets/b93b7c0e-3251-40c0-8d0a-0330d9499730)



