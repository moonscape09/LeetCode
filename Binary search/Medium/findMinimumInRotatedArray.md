<h1>Question: <a href="https://leetcode.com/problems/search-in-rotated-sorted-array/description">Search in Rotated Sorted Array</a></h1>

```
class Solution {
public:
    int findMin(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] >= nums[right]) left = mid + 1;
            else right = mid;
        }
        return nums[left];
    }
};
```

**Data structures/Algorithms used**: Arrays, Binary search
**Time complexity**: O(log n) (n = length of parameter array: `nums`)

**Space complexity**: O(1)

**Time taken**: 30 mins

**Explanation:**
A binary search algorithm that locates the pivoted index, by looking for a position where `nums[left]` is larger than `nums[right]`. 

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [3,4,5,1,2] </code>  | 1 |
| <code>nums = [4,5,6,7,0,1,2]</code>  | 0 |
| <code>nums = [11,13,15,17] </code>  | 11 |

**Statistics:** Beats 100% of solutions in runtime and 78.89% of solutions in memory usage


