<h1>Question: <a href="https://leetcode.com/problems/maximum-average-subarray-i/description](https://leetcode.com/problems/contains-duplicate-ii/description">Contains Duplicate II</a></h1>

```
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        int left = 0, right = 0;

        unordered_set<int> set;

        while (right < nums.size()){
            if (right - left > k) set.erase(nums[left++]);
            if (set.contains(nums[right])) return true;
            set.insert(nums[right]);
            right ++;
        }
        return false;
    }
};
```

**Data structures/Algorithms used**: Sliding window, Set

**Time complexity**: O(n) (n = length of parameter array: `nums`)

**Space complexity**: O(k) (k = range of numbers that `nums[i]` can be)

**Time taken**: 20 mins

**Explanation:**
A fixed-size sliding window algorithm that initializes a set called `set`. As we traverse `nums`, we insert new values into this set. If our window size exceeds `k`, we shrink the window, removing any `left` values and then incrementing the `left` pointer.

Otherwise, if we encounter an element that already exists in `set`, while our window's size is <=`k`, then we return `true`. At the end of the loop, we return `false` as duplicates within our sliding window haven't been found.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [1,2,3,1] k = 3</code>  | true |
| <code>nums = [1,0,1,1] k = 1</code>  | true |
| <code>nums = [1,2,3,1,2,3] k = 2</code>  | false |



**Statistics:** Beats 92.81% of solutions in runtime and 76.84% of solutions in memory usage.

<img width="680" height="455" alt="image" src="https://github.com/user-attachments/assets/974b33a5-5587-43ce-9420-7d0c72ce2357" />



