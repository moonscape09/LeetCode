<h1>Question: <a href="https://leetcode.com/problems/binary-tree-inorder-traversal/description">In-order Traversal</a></h1>

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
    vector<int> traverse(TreeNode* root, vector<int>& values) {
        if (!root) return values;
        traverse(root->left, values);
        values.push_back(root->val);
        traverse(root->right, values);
        return values;
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> values;
        values = traverse(root, values);
        return values;
        
    }
};
```

**Data structures/Algorithms used**: Binary tree

**Time complexity**: O(n) (n = number of nodes in tree)

**Space complexity**: O(h)

**Time taken**: 8 mins

**Explanation:**
A recursive approach, that stops when we reach beyond a leaf. In-order traversals go to the left nodes first, then the middle and lastly the right. We mimic this order in the `traverse` helper function, where recursive call on the left child is made, and once that recursive call stack clears, then we add the current root's value to the `values` array (storing all the in-orderly traversed values). Lastly, we traverse the right side through a recursive call using the right node.

We pass in a reference to the `values` array, to preserve the original array in memory throughout the entire recursive stack.

The updated `values` array is returned in each recursive stack frame. Once the recursive traversal finishes, we return the final `values` array in the original function.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [1,null,2,3]</code>  | [1, 3, 2] |
| <code>root = [1,2,3,4,5,null,8,null,null,6,7,9]</code>  | [4,2,6,5,7,1,3,9,8] |
| <code>root = []</code>  | [] |
| <code>root = [1]</code>  | [1] |

**Statistics:** Beats 100% of solutions in runtime and 5.19% of solutions in memory usage

![image](https://github.com/user-attachments/assets/7a249030-a57b-404e-be0c-7e0dc3484de0)


