<h1>Question: https://leetcode.com/problems/ransom-note/</h1>

```
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        #Counter class creating a frequency dictionary of items
        magazine_counter = Counter(magazine)
        ransomNote_counter = Counter(ransomNote)
        for i in ransomNote_counter:
            if magazine_counter[i] < ransomNote_counter[i]:
                return True
            return False
```

**Data structures used**: Frequency dictionary

**Time complexity**: O(n+m) (n = length of ransomNote, m = length of magazine, Counter takes linear time)

**Space complexity**: O(1) (only 26 letters)

<h3>Function</h3>
Return <code>True</code>, if <code>ransomNote</code> can be constructed using some or all letters from <code>magazine</code>. False otherwise. Each letter from <code>magazine</code> is used once.


**Parameters:**
- <code>ransomNote</code>: string to see if it can be constructed from <code>magazine</code>'s letters
- <code>magazine</code>: string to see if it can construct <ransomNote> from it's letters.

**Variables:**
- <code>magazine_counter</code>: a dictionary mapping each letter in <code>magazine</code> to it's frequency in the string.

- <code>ransomNote_counter</code>: a dictionary mapping each letter in <code>ransomNote</code> to it's frequency in the string.

**Return value:**
- True or False

**Explanation:**
We create a frequency dictionary for the letters in both strings. We then iterate over the <code>ransomNote</code>'s dictionary to see if there is less of the current letter in <code>magazine</code> than <code>ransomNote</code>.

If the condition is satisfied, the function returns False. Otherwise it returns True (after the loop signifying every check in the loop was valid).

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>ransomNote = "a", magazine = "b"</code>  | False  |
| <code>ransomNote = "aa", magazine = "ab"</code>  | False  |
| <code>ransomNote = "aa", magazine = "aab"</code> | True |

**Statistics: ** Beat 33.33% of solutions in runtime and beat 100% of solutions in memory usage :).

<img width="369" alt="image" src="https://github.com/moonscape09/LeetCode/assets/101025804/34a3050c-fe8d-46fe-a439-e8d7a1c8d7c9">
