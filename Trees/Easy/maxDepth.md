<h1>Question: <a href="https://leetcode.com/problems/maximum-depth-of-binary-tree/description/">Max Depth of Binary Tree</a></h1>

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
    int maxDepth(TreeNode* root) {
        int left = 0, right = 0;

        if (!root) return 0;
        
        if (root->left) left += maxDepth(root->left);
        
        if (root->right) right += maxDepth(root->right);

        return max(left + 1, right + 1);
    }
};
```

**Data structures/Algorithms used**: Binary tree

**Time complexity**: O(n) (n = number of nodes in binary tree)

**Space complexity**: O(h) (h = height of binary tree)

**Time taken**: 5 mins

**Explanation:**
A recursive algorithm that checks if the current node in the current stack frame has left/right children, updating and returning the max between the `left` and `right` variables. 

Both variables are added by one in the return, as a way to increment the depth.

Base case is when the root doesn't exist, hence the recursion stops after a leaf has been reached.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [3,9,20,null,null,15,7]</code>  | 3 |
| <code>root = [1,null,2]</code>  | 2 |

**Statistics:** Beats 100% of solutions in runtime and 75.52% of solutions in memory usage
