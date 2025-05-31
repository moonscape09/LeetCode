<h1>Question: <a href="https://leetcode.com/problems/move-zeroes/description/">Move Zeroes</a></h1>

```
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        /* 
        Base case: if nums doesn't have 0s, return nums
        If nums.size() == 1, return nums
        */

        int ptr_one = 0;
        int ptr_two = 1;
        int tmp = 0;

        if (nums.size() == 1) return;

        while (ptr_two < nums.size()) {
            if (nums[ptr_one] != 0) {
                ptr_one ++;
                ptr_two ++;
                continue;
            }

            if (nums[ptr_two] == 0) {
                ptr_two ++;
                continue;
            }
            
            // swap values at ptr_one and ptr_two
            tmp = nums[ptr_one];
            nums[ptr_one] = nums[ptr_two];
            nums[ptr_two] = tmp;

            ptr_one ++;
            ptr_two ++;
        }
    }
};
```

**Data structures/Algorithms used**: Array, Two-Pointers

**Time complexity**: O(n) (n = length of parameter array: `nums`)

**Space complexity**: O(1)

**Time taken**: 15 mins

**Explanation:**
A single pass two-pointer approach. First a base case is checked, where if `nums` has only one element, nothing has to be done.

Next, we loop through the `nums` array, until `ptr_two` approaches the last element. `ptr_one` is used to detect 0s, and once it points to a 0, `ptr_two` looks for the next non-zero element. Once found, the values on both pointers switch.

Looking at the cases within the while loop, we increment both pointers if `ptr_one` does NOT point to a 0. This ensures `ptr_two` stays ahead, as it's job is to find and point to the next non-zero element which will be swapped from right to left. So `ptr_two` keeps incrementing until a non-zero element is found.

After the swap, both pointers are incremented to look for other zeroes and non-zeroes to swap, if applicable.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [0,1,0,3,12]</code>  | [1,3,12,0,0] |
| <code>nums = [0]</code>  | [0] |
| <code>nums = [0,0]</code> | [0,0] |

**Statistics:** Beats 100% of solutions in runtime and 49.62% of solutions in memory usage



