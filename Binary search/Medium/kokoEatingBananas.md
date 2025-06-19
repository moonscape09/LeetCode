<h1>Question: <a href="https://leetcode.com/problems/koko-eating-bananas/description/">Koko Eating Bananas</a></h1>

```
class Solution {
public:
    int minEatingSpeed(vector<int>& piles, int h) {

        int left = 1;
        int right = *max_element(piles.begin(), piles.end());
        
        while (left < right) {
            int k = left + (right - left) / 2;

            int hours = 0;
            for (int i : piles) hours += i / k + (i % k != 0);

            if (hours <= h) right = k;
            else left = k + 1;
        }

        return left;
    }
};
```

**Data structures/Algorithms used**: Binary search

**Time complexity**: O(n*logm) (n = number of piles, m = largest pile)

**Space complexity**: O(1)

**Time taken**: 35 mins

**Explanation:**
A binary search algo that initializes two pointers, `left` and `right`, assigning them to 0 and the maximum pile size in `piles`, respectively.

Then the binary search algo is used to get a midpoint, `k`, as the eating rate. This rate then is used to compute the number of hours to consume all the piles, iteratively. The `hours += i \ k + (i % k != 0)` essentially adds 1 to `i \ k` if `i` is NOT divisible by `k` (variation of getting the ceiling of integer division). 

If the computed `hours` is less than or equal `h`, meaning that the rate is too quick or just right, then the search space reduces to the first half of the range. We still continue the search if `hours == h` as it may be possible to find a smaller rate that can get us the same hours, and we want to return the minimum sufficient rate.

Otherwise, if the `computed` hours is greater than to `h`, that means our rate is too slow and we must look at the upper half of the range.

Ultimately, we return `left`, as it will represent the minimum valid rate. 
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>piles = [3,6,7,11] h = 8</code>  | 4 |
| <code>piles = [30,11,23,4,20] h = 5</code>  | 30 |
| <code>piles = [30,11,23,4,20] h = 6</code>  | 23 |
| <code>piles = [312884470] h = 312884471</code>  | 2 | 
| <code>piles = [332484035,524908576,855865114,632922376,222257295,690155293,112677673,679580077,337406589,290818316,877337160,901728858,679284947,688210097,692137887,718203285,629455728,941802184] h = 823855818</code>  | 14 |



**Statistics:** Beats 96.49% of solutions in runtime and 96.55% of solutions in memory usage

![image](https://github.com/user-attachments/assets/3a229e80-298b-4dee-8fd4-18da13d04644)
