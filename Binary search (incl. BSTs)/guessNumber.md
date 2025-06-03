<h1>Question: <a href="https://leetcode.com/problems/guess-number-higher-or-lower/description">Guess Number</a></h1>

```
/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is higher than the picked number
 *			      1 if num is lower than the picked number
 *               otherwise return 0
 * int guess(int num);
 */

class Solution {
public:
    int guessNumber(int n) {
        int left = 0;
        int right = n;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int result = guess(mid);

            if (result == 0) {
                return mid;
            } else if (result == 1) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
        
    }
};
```

**Data structures/Algorithms used**: Binary search

**Time complexity**: O(log n)

**Space complexity**: O(1)

**Time taken**: 2 mins

**Explanation:**
A simple binary search solution. If the `guess` API returns 0, the guessed number is returned. If API returns -1 (guess > target), search space is set to lower half, else if API returns 1 (guess < target) then search space is set to upper half in the range of `n`.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>n = 10, pick = 6</code>  | 6 |
| <code>n = 1, pick = 1</code>  | 1 |
| <code>n = 2, pick = 1</code>  | 1 |

**Statistics:** Beats 100% of solutions in runtime and 71.64% of solutions in memory usage

![image](https://github.com/user-attachments/assets/cc972659-8e16-4329-b2de-9b0efdd2c9c3)


