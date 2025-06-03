<h1>Question: <a href="https://leetcode.com/problems/search-insert-position/description">Search Insert</a></h1>

```
class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] > target) right = mid - 1;
            else left = mid + 1;
        }
        return left;
    }
};
```

**Data structures/Algorithms used**: Array, Binary search

**Time complexity**: O(log n)

**Space complexity**: O(1)

**Time taken**: 5 mins

**Explanation:**
A simple binary search solution. Looks for the target if it exists using a basic binary search approach. If target is not found, then the left index (where it would be inserted to maintain sort) is returned.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [1,3,5,6] target = 5 </code>  | 2 |
| <code>nums = [1,3,5,6], target = 2</code>  | 1 |
| <code>nums = [1,3,5,6], target = 7</code>  | 4 |

**Statistics:** Beats 100% of solutions in runtime and 76.50% of solutions in memory usage

![image](https://github.com/user-attachments/assets/bdd4e64d-8892-4abc-a3f4-af2549465fee)


