<h1>Question: <a href="https://leetcode.com/problems/longest-substring-without-repeating-characters/description/">Length of Longest Substring without Repeating Characters</a></h1>

```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int left = 0, right = 0;

        map<char, int> freq;

        int len = 0;
        while (right < s.size()) {
            freq[s[right]] ++;
            while (freq[s[right]] > 1) freq[s[left++]] --;
            len = max(len, right - left + 1);
            right ++;
        }

        return len;
    }
};
```

**Data structures/Algorithms used**: Sliding window, Hashmap, Array

**Time complexity**: O(n) (n = length of parameter string: `s`)

**Space complexity**: O(alphabet-size) (alphabet-size = # of distinct characters in `s`)

**Time taken**: 5 mins

**Explanation:**
A variable-size sliding window algorithm that expands the window (increments the `right`), storing characters in a frequency map, and shrinks the window (increments the `left`) if a duplicate is found until everything is unique again (no repeating characters). 

If the condition of no repeating characters is met, the current longest substring length is stored in `len` as the running state. This state updates whenever a longer substring with no repeated characters is found.

At the end of the loop, `len` is returned, with the length of the longest substring with no repeating characters in `s`.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>s = ""abcabcbb"</code>  | 3 |
| <code>s = "bbbbb"</code>  | 1 |
| <code>s = "pwwkew"</code>  | 3 |


**Statistics:** Beats 77.51% of solutions in runtime and 43.37% of solutions in memory usage
