<h1>Question: <a href="https://leetcode.com/problems/successful-pairs-of-spells-and-potions/">Successful Pairs</a></h1>

```
class Solution {
public:
    vector<int> successfulPairs(vector<int>& spells, vector<int>& potions, long long success) {
        int m = potions.size();
        sort(potions.begin(), potions.end());
        vector<int> pairs;
        for (int i = 0; i < spells.size(); i++) {
            int successfulPairs = 0;
            int left = 0;
            int right = m - 1;

            while (left <= right) {
                int mid = left + (right - left) / 2;

                if ((long long) potions[mid] * spells[i] >= success) {
                    successfulPairs = m - mid;
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
            pairs.push_back(successfulPairs);
        }

        return pairs;
    }
};
```

**Data structures/Algorithms used**: Arrays, Binary search

**Time complexity**: O(n log m) (n = length of parameter array: `spell`, m = length of parameter array: `potions`)

**Space complexity**: O(n) (n = length of parameter array: `spell`)

**Time taken**: 20 mins

**Explanation:**
A binary search algorithm, that sorts the potions first. For every spell, the binary search finds the index with the smallest possible potion whose product with the current spell's value is greater than `success`. Once this index is found, given that potions is sorted, we can deduce that the rest of the potions after also make successful pairs. Hence, we simply take this number of potions by subtracting the last index of the sorted potions array and subtracting that with the newfound index. Lastly, this difference is stored in the `i`th position of `pairs`.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>spells = [5,1,3], potions = [1,2,3,4,5], success = 7 </code>  | [4,0,3] |
| <code>spells = [3,1,2], potions = [8,5,8], success = 16 </code>  | [2,0,2] |
| <code>spells = [40,11,24,28,40,22,26,38,28,10,31,16,10,37,13,21,9,22,21,18,34,2,40,40,6,16,9,14,14,15,37,15,32,4,27,20,24,12,26,39,32,39,20,19,22,33,2,22,9,18,12,5], potions = [31,40,29,19,27,16,25,8,33,25,36,21,7,27,40,24,18,26,32,25,22,21,38,22,37,34,15,36,21,22,37,14,31,20,36,27,28,32,21,26,33,37,27,39,19,36,20,23,25,39,40], success = 600 </code>  | [48,0,32,37,48,22,33,47,37,0,43,6,0,46,0,21,0,22,21,14,46,0,48,48,0,6,0,0,0,3,46,3,45,0,34,20,32,0,33,47,45,47,20,18,22,45,0,22,0,14,0,0] |

**Statistics:** Beats 66.93% of solutions in runtime and 24.64% of solutions in memory usage

