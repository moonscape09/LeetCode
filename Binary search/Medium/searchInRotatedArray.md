<h1>Question: <a href="https://leetcode.com/problems/search-in-rotated-sorted-array/description">Search in Rotated Sorted Array</a></h1>

```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int n = nums.size();

        int left = 0;
        int right = nums.size() - 1;

        while (nums[left] > nums[right]) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right]) left = mid + 1;
            else if (nums[mid] < nums[right]) right = mid;
        }
        
        int pivot = left;
        left = 0;
        right = nums.size() - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int rotatedMid = (mid + pivot) % n;
            
            if (nums[rotatedMid] > target) right = mid - 1;
            else if (nums[rotatedMid] < target) left = mid + 1;
            else return rotatedMid;
        }

        return -1;
    }
};
```

**Data structures/Algorithms used**: Arrays, Binary search

**Time complexity**: O(log n) (n = length of parameter array: `nums`)

**Space complexity**: O(1)

**Time taken**: 30 mins

**Explanation:**
A binary search algorithm that locates the pivoted index, by looking for a position where `nums[left]` is smaller than `nums[right]`. 

Once this position is found, it is stored in `pivot`. Now a binary search algo is done, accounting for the `pivot` factor to locate the target (in case of an overflow, we use `% n`). If the `target` is found, then we return the index of it, otherwise we return -1.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [4,5,6,7,0,1,2] target = 0</code>  | 4 |
| <code>nums = [1] target = 0</code>  | -1 |
| <code>nums = [3,5,1] target = 1</code>  | 2 |

**Statistics:** Beats 100% of solutions in runtime and 33.06% of solutions in memory usage


