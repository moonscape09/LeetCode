<h1>Question: <a href="https://leetcode.com/problems/jump-game/description/">Jump-Game</a></h1>

```
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        currentJump = nums[0]
        for i in range(1, len(nums)):
            if currentJump == 0:
                return False

            if nums[i] >= currentJump:
                currentJump = nums[i]
            else:
                currentJump -= 1

        return True
            
```

**Data structures used**: Array

**Time complexity**: O(n)

**Space complexity**: O(1)

<h3>Function</h3>
Given an array of integers `nums` we are initially positioned at array's first index where each element in the array represents the maximum
jump length at that position (i.e if element = 3, one can traverse three following indices max within the array). Returns true if the last index 
can be reached and false otherwise


**Parameters:**
- <code>nums</code>: non-empty array of integers

**Variables:**
- <code>currentJump</code>: an integer variable representing the number of jumps left at the current position

**Return value:**
- <code>True/False</code>

**Explanation:**
A greedy approach is used here to check if the jumps run out before reaching the last index. That is, 
`currentJump == 0` while we are not on the last index.

`currentJump` is initially set to the first index of the `nums` array. Afterwards, we traverse the array from the second element onwards. We have a basic
case to check if `currentJump` is 0 and we return false to terminate the loop and the function.

Next, we see if the current element is larger than `currentJump`, and under this condition we reassign `currentJump` to this element so that we 
don't run out of jumps. Overall, what we are doing is finding the largest number within the maximum jump range from the current position and reassigning to that number.

Moreover, if the element's jump range is smaller than our `currentJump`, we count that as a jump and decrement it as there is no point in reassignment either to a smaller value
and potentially being at risk of not reaching the end (consider the case: `[3,4,2,0,0,1]` where we are at element `2`).

Once the array has been fully traversed, we have bypassed the terminating step and therefore we can return True.

**Example Test Cases:**

| Input  | Output |
| ------------- | ------------- |
| <code>nums = [0]</code>  | true |
| <code>nums = [1,2,3,4,5]</code>  | true |
| <code>prices = [1,0,2,3]</code> | false |
| <code>prices = [3,4,2,0,0,1]</code> | true |
| <code>nums = [2,3,1,1,4]</code> | true |
| <code>nums = [3,2,1,0,4]</code> | false |

**Statistics**: Beat 99% of solutions in runtime and 63% of solutions in memory usage.

<img width="370" alt="image" src="https://github.com/moonscape09/LeetCode/assets/101025804/b24c4ed5-2afd-473c-a992-aaf9b12d004a">
