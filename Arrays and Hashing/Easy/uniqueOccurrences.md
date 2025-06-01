<h1>Question: <a href="https://leetcode.com/problems/unique-number-of-occurrences/description">Unique Number of Occurrences</a></h1>

```
class Solution {
public:
    bool uniqueOccurrences(vector<int>& arr) {
        unordered_map<int, int> freq_map;
        for (auto i : arr) {
            freq_map[i] ++;
        }

        unordered_map<int, int> occurrences;
        for (auto u : freq_map) {
            occurrences[u.second] ++;

            if (occurrences[u.second] > 1) return false;
        }

        return true;
    }
};
```

**Data structures/Algorithms used**: Arrays, Hash maps

**Time complexity**: O(n) (n = length of parameter array: `arr`)

**Space complexity**: O(n) (n = length of parameter array: `arr`)

**Time taken**: 15 mins

**Explanation:**
A multi-pass algorithm that first stores the frequency of elements in `arr` in `freq_map`.

Then, `freq_map` is iterated through, to store the frequency of the values of this map onto `occurrences`. If there are multiple occurrences of a frequency in `freq_map`, then we return false.

Otherwise, after the iteration, we return true.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>arr = [1,2,2,1,1,3]</code>  | true |
| <code>arr = [1,2]</code>  | false |
| <code>arr = [-3,0,1,-3,1,1,1,-3,10,0]</code> | true |

**Statistics:** Beats 100% of solutions in runtime and 78.95% of solutions in memory usage

<img width="693" alt="image" src="https://github.com/user-attachments/assets/1eed2a25-efe9-4262-8a19-0b4d01c9bb35" />


