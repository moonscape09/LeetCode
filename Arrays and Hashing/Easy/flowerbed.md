<h1>Question: <a href="https://leetcode.com/problems/can-place-flowers/description/">Can Place Flowers</a></h1>

```
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        for (int i = 0; i < flowerbed.size(); i++) {
            if (flowerbed[i] == 0){
                bool leftPlotEmpty = (i == 0) || (flowerbed[i - 1] == 0);
                bool rightPlotEmpty = (i == flowerbed.size() - 1) || (flowerbed[i+1] == 0);

                if (leftPlotEmpty && rightPlotEmpty) {
                    flowerbed[i] = 1;
                    n --;
                }
            }
        }
        return n <= 0;
    }
};
```

**Data structures used**: Array

**Time complexity**: O(n) (n = length of parameter array: `flowerbed`)

**Space complexity**: O(1)

**Time taken**: 15 mins (most of spent on refactoring tbh)

**Explanation:**
A single pass algorithm. Checks for if the current plot we are on is empty (`flowerbed[i] == 0`) and I initialize two booleans `leftPlotEmpty`, `rightPlotEmpty` to check if the left and right plots are also empty. If the case is true, then we can place a flower on the current plot, otherwise we are breaking the no-adjacent-flowers rule. 

If we can place a flower on the current plot, we set the current plot to full `flowerbed[i] == 1` and we decrement `n`. This reduces the remaining to-be-planted flowers we have.

Ultimately at the end of the pass, if `n > 0`, this means we still have some flowers remaining to-be-planted. This implies that there weren't enough plots to plant `n` flowers while adhering to the no-adjacent-flowers rule. 

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>flowerbed = [1,0,0,0,1], n = 1</code>  | true |
| <code>ransomNote = "[1,0,0,0,1]"</code>  | false |
| <code>ransomNote = "[1,0,0,0,0,1,0,0,0]"</code> | false |

**Statistics:** Beats 100% of solutions in runtime and 97.35% of solutions in memory usage
