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
    TreeNode* deleteNode(TreeNode* root, int key) {
        if (!root) return nullptr;

        if (root->val < key) {
            root->right = deleteNode(root->right, key);
        } else if (root->val > key) {
            root->left = deleteNode(root->left, key);
        } else {
            TreeNode* temp;
            if (!root->left && !root->right) {
                delete root;
                return nullptr;
            } else if (!root->right) {
                temp = root->left;
                delete root;
                return temp;
            } else if (!root->left) {
                temp = root->right;
                delete root;
                return temp;
            } else {

                // find in-order successor
                temp = root->right;
                while (temp->left != nullptr) temp = temp->left;

                // update root's value
                root->val = temp->val;
                root->right = deleteNode(root->right, temp->val);
            }
        }
        return root;
    }
};
```

**Data structures/Algorithms used**: Binary search tree

**Time complexity**: O(h) (h = height of tree)

**Space complexity**: O(h) (h = height of tree)

**Time taken**: 30 mins

**Explanation:**
The solution traverses through the tree to find the node to delete. Following the BST property, if the root's value is less than the key, then the right subtree is traversed, and if the root's value is greater than the key, the left subtree is traversed.

If node is found, there are 4 cases to consider:

1) if the node has no children, the node is simply deleted and a nullptr is returned to recursive call it is in.
2) if the node has only a left child, a temporary variable is set to the left subtree's root. The current node is then deleted and the left subtree's root (stored in `temp`) is returned to the recursive call it's in. 
3) if the node has only a right child, the converse of the previous case applies.
4) if the node has two children, then the in-order successor (smallest value in the right subtree) must be found. To do this, we simply find the leftmost leaf in the right subtree (keep traversing to the left node until there is no left node remaining). The current node's value is then updated to this successor, and right subtree is set to a recursive call to remove the original node the successor value was taken from (to omit duplicates).

The functions returns the `root` itself, as the possibly updated BST.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>root = [5,3,6,2,4,null,7] key = 3</code>  | [5,4,6,2,null,null,7] |
| <code>root = [5,3,6,2,4,null,7] key = 3</code>  | [5,3,6,2,4,null,7] |
| <code>root = [] key = 0</code>  | [] |
| <code>root = [1] key = 0</code>  | [1] |
| <code>root = [2,1,3,null,null,null,5,4,6] key = 3</code>  | [2,1,5,null,null,4,6] |



**Statistics:** Beats 100% of solutions in runtime and 93.50% of solutions in memory usage
![image](https://github.com/user-attachments/assets/72d07fa4-6ca0-478a-9780-e18425c29f83)

