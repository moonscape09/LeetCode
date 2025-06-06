<h1>Question: <a href="https://leetcode.com/problems/delete-node-in-a-bst/description">Delete Node in a BST</a></h1>

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
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        TreeNode* curr = root;
        if (!root) return new TreeNode(val);

        while (curr->left || curr->right) {
            if (curr->val < val) {
                if (!curr->right) break;
                curr = curr->right;
            } else if (curr->val > val) {
                if (!curr->left) break;
                curr = curr->left;
            }
        }
        
        if (curr->val < val) curr->right = new TreeNode(val);
        else if (curr->val > val) curr->left = new TreeNode(val);
        
        return root;
    }
};
```

**Data structures/Algorithms used**: Binary search tree

**Time complexity**: O(h) (h = height of tree)

**Space complexity**: O(1)

**Time taken**: 15 mins

**Explanation:**
Base case is that if there is no root, then we set the new node to the root with the new value.

Otherwise we traverse the BST until a node with no children is found. Once this node is reached, we compare the value of the node with the value to insert, and if the new value is larger, the node's right child is created with the value. Conversely, if the new value is smaller, then the node's left child is created with the value.


**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [4,2,7,1,3] val = 5</code>  | [4,2,7,1,3,5] |
| <code>root = [40,20,60,10,30,50,70] val = 25</code>  | [40,20,60,10,30,50,70,null,null,25] |
| <code>root = [4,2,7,1,3,null,null,null,null,null,null] val = 5</code>  | [4,2,7,1,3,5] |
| <code>root = [8,null,55,39,null,11,null,null,23,null,null] val = 17</code>  | [8,null,55,39,null,11,null,null,23,17] |
| <code>root = [5,null,14,10,77,null,null,null,95,null,null] val = 4</code>  | [5,4,14,null,null,10,77,null,null,null,95] |



**Statistics:** Beats 100% of solutions in runtime and 98.21% of solutions in memory usage

![image](https://github.com/user-attachments/assets/9bbbf988-1f7a-471f-b8f4-a6d1918679bc)


