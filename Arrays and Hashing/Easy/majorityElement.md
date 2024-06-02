<h1>Question: <a href="https://leetcode.com/problems/majority-element/description/">Majority Element</a></h1>

```
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        majorityElem = 0
        for i in nums:
            if count == 0:
                majorityElem = i
            
            if i == majorityElem:
                count += 1
            else:
                count -= 1
        return majorityElem
```

**Data structures used**: Array

**Time complexity**: O(n) (n = length of parameter array: `nums`)

**Space complexity**: O(1) (introduced two integer variables: `count`, `majorityElem`)

<h3>Function</h3>
Returns the majority element (the element that appears **more than** <code>⌊n / 2⌋</code> times) given a non-empty array <code>nums</code> of size <code>n</code>. Given the assumption that there is always a majority element in the <code>nums</code> array.


**Parameters:**
- <code>nums</code>: array of integers where the majority element has to exist

**Variables:**
- <code>count</code>: a counter variable keeping count of the current <code>majorityElem</code>

- <code>majorityElem</code>: an integer representing the current majority element during iteration

**Return value:**
- <code> majorityElem: int </code>

**Explanation:**
We use the Boyer-Moote voting algorithm. Two important variables are needed here, a counter variable (`count`) that increments/decrements the occurrence of a 'candidate' variable (`majorityElem`). This variable increments for every occurrence of the candidate found, and decrements for any other occurrence. Once this count equates to 0, the candidate switches to the current variable in the array that we are on. Given the assumption that the majority element occurs **more than** <code>⌊n / 2⌋</code> times, there must be a candidate element whose count will never reach 0. Consequently, there can't be any other possible candidates. Thus, after traversing the entire array once, we can simply just return this candidate that `majorityElem` is set to.  

**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums = [1,1,2,2,3,3,4,4,4,4,4,4,4]</code>  | 4 |
| <code>ransomNote = "[1,1,1,1]"</code>  | 1 |
| <code>ransomNote = "[10]"</code> | 10 |

**Statistics:** Beat 96% of solutions in runtime and 71% of solutions in memory usage

<img width="372" alt="image" src="https://github.com/moonscape09/LeetCode/assets/101025804/902a03f0-4e8b-43db-afcc-1575af3e2cc1">
