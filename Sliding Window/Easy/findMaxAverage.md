<h1>Question: <a href="https://leetcode.com/problems/permutation-in-string/description">Permutation in String</a></h1>

```
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {
        int left = 0, right = k - 1;
        double maxAvg = -10000, currAvg = 0;

        for (int i = left; i < right; i++) currAvg += nums[i];

        while (right < nums.size()) {
            currAvg += nums[right];
            if (right - left + 1 > k) {
                currAvg -= nums[left];
                left ++;
            }
            maxAvg = max(maxAvg, currAvg / k);
            right ++;
        }

        return maxAvg;
    }
};
```

**Data structures/Algorithms used**: Sliding window

**Time complexity**: O(n) (n = length of parameter array: `nums`)

**Space complexity**: O(1)

**Time taken**: 15 mins

**Explanation:**
A fixed-size sliding window algorithm that initializes `maxAvg` to the smallest possible value as per the problem's assumptions (-10^4 < nums[i] < 10^4). The `left` and `right` pointers define our k-sized window, and the average of the first window is stored in `currAvg`. 

Now we iterate our pointers, updating the running state, `currAvg` and shrinking whenever our window's length exceeds `k`. The `maxAvg` is always updated in case a new max is found.

After the loop, we return the `maxAvg`.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [1,12,-5,-6,50,3] k = 4</code>  | 12.75 |
| <code>nums = [5] k = 1</code>  | 5 |



**Statistics:** Beats 100% of solutions in runtime and 44.38% of solutions in memory usage.

![image](https://github.com/user-attachments/assets/85a31d04-f91f-444a-8c53-1e53c715f0bd)



