<h1>Question: <a href="https://leetcode.com/problems/permutation-in-string/description">Permutation in String</a></h1>

```
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        int num = s1.size(); // length of sliding window

        int left = 0, right = 0;

        unordered_map<char, int> freq;
        unordered_map<char, int> freq_2;
        for (char s : s1) freq_2[s]++;

        while (right < s2.size()) {
            freq[s2[right]]++;
            if (right - left + 1 > num) {
                freq[s2[left]] --;
                if (!freq[s2[left]]) freq.erase(s2[left]);
                left ++;
            } 
            if (freq == freq_2) return true; // permutation found
            right ++;
        }

        return false;
         
    }
};
```

**Data structures/Algorithms used**: Sliding window, Hashmap, String

**Time complexity**: O(n) (n = length of parameter string: `s2`)

**Space complexity**: O(alphabet-size) (alphabet-size = # of distinct characters in `s1`/`s2`)

**Time taken**: 10 mins

**Explanation:**
A fixed-size sliding window algorithm that first stores a frequency map of the permutation string `s1` in `freq_2`. Then we slide the window throughout `s2`, maintaining the size of the window to match the size of the permutation (`s1`). We update the frequency map of this window every iteration.

If this size is exceeded, we decrement the `left` key's frequency and then shrink the window. If the `left` key's frequency is 0, we omit the key-value pair from the map as it isn't needed.

In the case that our window's size matches that of `s1`, then we compare the unordered frequency map of our window to that of our permutation string. If the maps are equal, we discover that `s1` is a permutation of `s2` and return false. Otherwise, the iteration keeps going.

If we reach after the loop, we have found no matching permutations of `s2` against `s1`, so we simply return false.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>s1 = "ab" s2="eidbaooo"</code>  | true |
| <code>s1 = "ab" s2="eidboaoo"</code>  | false |


**Statistics:** Beats 69.71% of solutions in runtime and 24.46% of solutions in memory usage.


