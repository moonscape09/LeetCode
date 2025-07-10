<h1>Question: <a href="https://leetcode.com/problems/find-all-anagrams-in-a-string/description/">Find All Anagrams in a String</a></h1>

```
class Solution {
public:
    vector<int> findAnagrams(string s, string p) {
        unordered_map<char, int> freq_p, freq_s;

        for (char c : p) freq_p[c]++;

        int left = 0, right = 0, n = p.size();

        vector<int> indices;

        while (right < s.size()) {
            freq_s[s[right]]++;
            if (right - left + 1 > n) {
                freq_s[s[left]]--;
                if (!freq_s[s[left]]) freq_s.erase(s[left]); // remove the key-value pair
                left ++;
            }
            if (freq_s == freq_p) indices.push_back(left);
            right ++;
        }

        return indices;

    }
};
```

**Data structures/Algorithms used**: Sliding window, Hashmap, String

**Time complexity**: O(n) (n = length of parameter string: `s`)

**Space complexity**: O(alphabet-size) (alphabet-size = # of distinct characters in `s`/`p`)

**Time taken**: 20 mins

**Explanation:**
A fixed-size sliding window algorithm that first stores a frequency map of the `p` string containing the anagram to check against. Then we traverse through the `s` string, storing the frequency of the current character as we increment our sliding window. Under the condition that our window is larger than the length of `s` (which indicates our window's anagram isn't valid anymore as it is longer), then we shrink and decrement the frequency of the `left` characters. We erase any key-value pairs that have value `0` in order to have a valid comparison between the frequency map of `p` and that of our current window.

We then compare the frequency maps of `p` and our current window, and if they match, that means our current window has a valid anagram, and hence, we append the starting index of this window, `left`, to the list of `indices` to return.

At the end of the loop, we return our list of `indices`.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>s = "cbaebabacd" p="abc"</code>  | [0, 6] |
| <code>s = "abab" p="ab"</code>  | [0,1,2] |


**Statistics:** Beats 31.47% of solutions in runtime and 21.33% of solutions in memory usage.


