<h1>Question: <a href="https://leetcode.com/problems/maximum-length-substring-with-two-occurrences/description">Maximum Length Substring With Two Occurrences</a></h1>

```
class Solution {
public:
    int maximumLengthSubstring(string s) {
        int left = 0, right = 0, maxLen = 0;
        map<char, int> freq;

        while (right < s.size()) {
            freq[s[right]]++;
            while (freq[s[right]] > 2) freq[s[left++]]--;
            maxLen = max(right - left + 1, maxLen);
            right ++;
        }
        return maxLen;
    }
};
```

**Data structures/Algorithms used**: Sliding window, Hash map

**Time complexity**: O(n) (n = length of parameter string: `s`)

**Space complexity**: O(k) (k = length of alphabet)

**Time taken**: 15 mins

**Explanation:**
A variable-sized sliding window algorithm that updated the frequency map of characters in the current sliding window. If there is a frequency that exceeds 2, violating our constraint of at most 2 occurrences, we decrement the frequency of `s[left]` character before shrinking the window.

On every iteration, we update the `maxLen` to remain as the longest substring with at most two occurrences of each character.

After the loop, we return the `maxLen` state.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>s="bcbbbcba"</code>  | 4 |
| <code>s="aaaa"</code>  | 2 |

**Statistics:** Beats 100% of solutions in runtime and 65.24% of solutions in memory usage.

<img width="714" height="403" alt="image" src="https://github.com/user-attachments/assets/5dee6035-52a0-4bd2-ade1-b3219f508494" />



