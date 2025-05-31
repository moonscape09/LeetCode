<h1>Question: <a href="https://leetcode.com/problems/is-subsequence/description/">Is Subsequence</a></h1>

```
class Solution {
public:
    bool isSubsequence(string s, string t) {
        vector<int> indices = {-1}; 
        for (char c : s) {
            for (int i = indices[indices.size() - 1] + 1; i < t.size(); i ++) {
                if (t[i] == c) {
                    indices.push_back(i);
                    break;
                }
            }
        }
        return indices.size() == s.size() + 1;
    }
};
```

**Data structures/algorithms used**: Array, Two-Pointers

**Time complexity**: O(m * n) (n = length of `s`, m = length of `t`)

**Space complexity**: O(n)

**Time taken**: 15 mins

**Explanation:**
A two pointers approach, where the first pointer points to characters in `s` For every character in `s`, the second pointer passes through `t`. Every pass, the second pointer starts after the last stored index in the `indices` vector.

The `indices` vector stores all character matches between `t` and `s`. To maintain the relative order, the second pointer starts after the last stored index to find the remaining matches. `indices` is initialized to store -1, so that on the first iteration, the second pointer starts at 0.

If `s` is a subsequence of `t`, then `indices` must have just one more element than `s` (to account for the -1 that was initially placed in it). The function returns whether this case is true or false.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>s = "abc" t = "ahbgdc" </code>  | true |
| <code>s = "axc" t = "ahbgdc"</code>  | false |
| <code>s = "aza" t = "abzba"</code> | true |

**Statistics:** Beats 100% of solutions in runtime and 31.51% of solutions in memory usage
![image](https://github.com/user-attachments/assets/8a63c8d8-8909-46d9-af1d-f465ac405353)


