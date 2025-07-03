<h1>Question: <a href="https://leetcode.com/problems/minimum-size-subarray-sum/description">Minimum Size Subarray Sum</a></h1>

```
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int left = 0, right = 0, sum = 0, len = 100000;
        
        while (right < nums.size()) {
            sum += nums[right];
            while (sum >= target) {
                sum -= nums[left];
                len = min(len, right - left + 1);
                left ++;
            }
            right ++;
        }
        if (left == 0) return 0;

        return len;
    }
};
```

**Data structures/Algorithms used**: Sliding window, Array

**Time complexity**: O(n) (n = length of parameter array: `nums`)

**Space complexity**: O(n) (n = length of parameter array: `nums`)

**Time taken**: 20 mins

**Explanation:**
A variable-size sliding window algorithm that expands the window (increments the `right`), after updating the running state: `sum`, and shrinks the window (increments the `left`) if the running sum is greater than or equal to the target.

During the shrinking process, we keep updating the length to stay as the minimum sized subarray whose sum is >= `target`.

After the loop, we check for the case when the sum of the entire array, `nums` is less than the target, indicated by the `left` pointer being unmoved (no shrinking was done as the condition that the sum >= `target` was never met). Otherwise, at the end, the minimum length is returned.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [2,3,1,2,4,3] target = 7</code>  | 2 |
| <code>nums = [1,4,4] target = 4</code>  | 1 |
| <code>nums = [1,1,1,1,1,1,1,1] target = 11</code>  | 0 |


**Statistics:** Beats 100% of solutions in runtime and 96.93% of solutions in memory usage
