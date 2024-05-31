<h1>Question: https://leetcode.com/problems/valid-anagram/</h1>

```
class Solution {
public:
    bool isAnagram(string s, string t) {
        std::map<char, int> char_map;

        if (s.size() != t.size()) { // early check to see if the string sizes are different, hence not anagrams 
            return false;
        }
        
        for (char i : s) {
            char_map[i] ++;
        }

        for (char i : t) {
            char_map[i] --;
            if (char_map[i] < 0) {
                return false;
            }
        }

        for (auto const& x : char_map) {
            if (x.second != 0) {
                return false;
            }
        }
        return true;
    }
};
```
  
**Data structures used**: Map

**Time complexity**: O(n)

**Space complexity**: O(1) (given that there can be at most 256 unique characters)

<h3>Function</h3>
Return whether the string arguments <code>s</code> and <code>t</code> are anagrams as a boolean.


**Parameters:**
- <code>s</code>: the first string
- <code>t</code>: the second string

**Variables:**
- <code>char_map</code>: a frequency map for the different characters in the strings


**Explanation:**
First an early check is done to see if the lengths of the strings are different, which indicates they are not anagrams. This check saves the work involving the frequency map. 

Then, the frequency of all the characters in string <code>s</code> is checked for and the counts are incremented. Afterwards, the string <code>t</code> is traversed where the count for each character decrements upon every occurrence.

Lastly, the map is traversed to see if any of the values are not equal to 0, indicating that there may have been a surplus of characters in one of the strings compared to the other. Thus it would return false and terminate. Otherwise, both strings are anagrams
and at the end returns true.

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>t="anagram", s="nagaram"</code>  | true  |
| <code>t="car", s="rat"</code>  | false  |
| <code>t="debitcard" s="badcredit"</code> | true |

