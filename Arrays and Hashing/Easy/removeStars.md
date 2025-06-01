<h1>Question: <a href="https://leetcode.com/problems/removing-stars-from-a-string/description">Removing Stars From a String</a></h1>

```
class Solution {
public:
    string removeStars(string s) {
        stack<char> nonStars;
        for (int i = 0; i < s.size(); i ++) {
            if (s[i] != '*') {
                nonStars.push(s[i]);
            } else {
                nonStars.pop();
            }
        }

        string newS;
        while (!nonStars.empty()) {
            newS += nonStars.top();
            nonStars.pop();
        }

        reverse(newS.begin(), newS.end());

        return newS;
        
    }
};
```

**Data structures/Algorithms used**: Stack

**Time complexity**: O(n) (n = length of parameter string: `s`)

**Space complexity**: O(n) (n = length of parameter string: `s`)

**Time taken**: 15 mins

**Explanation:**
A push/pop algorithm involving stacks. The stack `nonStars` is being pushed to with letters from `s`. Every time a '*' is found, then `nonStars` is popped as a way of removing the left nearest non-star element.

Afterwards, a string is populated from popping from the stack, until it is empty. Since a stack follows a LIFO order, the string is reversed then returned, with all stars and their leftward nearest non-stars.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>s = "leet**cod*e"</code>  | "lecoe" |
| <code>s = "erase*****"</code>  | "" |

**Statistics:** Beats 88.04% of solutions in runtime and 35.46% of solutions in memory usage
