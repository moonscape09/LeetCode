<h1>Question: <a href="https://leetcode.com/problems/validate-binary-search-tree/description/">Validate BST</a></h1>

```
/**
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
    bool validateBST(TreeNode* root, long long minimum, long long maximum) {
        if (!root) return true;
        if (root->val <= minimum || root->val >= maximum) return false;

        return validateBST(root->left, minimum, root->val) && validateBST(root->right, root->val, maximum);
    }
    bool isValidBST(TreeNode* root) {
        return validateBST(root, LONG_MIN, LONG_MAX);
    }
};
```

**Data structures/Algorithms used**: Binary search tree

**Time complexity**: O(n) (h = height of tree)

**Space complexity**: O(h) (h = height of tree)

**Time taken**: 35 mins

**Explanation:**
A DFS-based approach that sets a dynamic range upon every recursive call. A helper called `validateBST` is set, with the following params:

`root`: the current node (will explain later)
`minimum`: the lower-bound of the dynamic range
`maximum`: the upper-bound of the dynamic range

We have two base cases. First we check if the current node exists (if we have reached beyond a leaf), and if it doesn't we just return true (this is valid as per the BST property). Next we check if the current node's value is not within the dynamic range (essentially checking for if the BST property is being violated), in which case we return false. This false return goes up the stack frame and warrants the whole tree not being a BST so ultimately, false will be the final output.

The recursive call sets this dynamic range. When going into the left child (`root->left`), the minimum stays as is (could be `LONG_MIN` or an ancestor node depending on where the node is on the tree), and the maximum is set to the `root->val`. This is to set an upper bound in the range such that any value in the left subtree, HAS to be smaller than this value, as per the BST property. The converse applies for going to the right child (`root->right`), where the maximum stays as is and the minimum is set to the `root->val` as a lower bound such that any value in the right subtree HAS to be larger than this value to maintain the BST property.

We return an `&&` statement, so that the `false` state is maintained (when an invalid node is found that breaks the BST) throughout the call stack.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [2,1,3]</code>  | true |
| <code>root = [5,1,4,null,null,3,6]</code>  | false |
| <code>root = [2,2,2]</code>  | false |



**Statistics:** Beats 100% of solutions in runtime and 47.07% of solutions in memory usage

