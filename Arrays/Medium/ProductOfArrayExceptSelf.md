<h1>Question: <a href="https://leetcode.com/problems/product-of-array-except-self/description/">Product Of Array Except Self</a></h1>

```
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        answer = [0] * n
        answer[0] = nums[0]
        for i in range(1, n):
            answer[i] = answer[i-1] * nums[i]
        for i in range(n-2, -1, -1):
            nums[i] = nums[i+1] * nums[i]
        nums[0] = nums[1]
        for i in range(1, n - 1):
            nums[i] = answer[i-1] * nums[i+1]
        nums[n - 1] = answer[n-2]
        answer = nums # not needed but stays consistent with problem description
        return answer
```

**Data structures used**: Array

**Time complexity**: O(n)

**Space complexity**: O(1) (we are given a follow-up on the description that the returned array does not count as extra space, though overall would be O(n))

<h3>Function</h3>
Given an array of integers `nums` it returns an array `answer` where `answer[i]` is equal to the product of all the elements in the `nums` array except `num[i]`, itself.


**Parameters:**
- <code>nums</code>: array with at least two integers that are `<=30` and `>=-30` to guarantee that products fit within a 32-bit integer

**Return value:**
- <code>answer</code>: array with all the products except self

**Explanation:**
Here we are using a prefix/suffix product approach that would get the product of elements preceding and succeeding the current element respectively, and multiplying them both to get the desired product except self.

First we create an `n`-sized array, `answer` that we have to return, having the same first element as the `nums` array.

On the first pass, get all the prefix products. That is, the product of preceding elements for every element in the `nums` array. We store all these prefix products in the answer array.

On the second pass, we get all the suffix products. That is, the product of succeeding elements for every element in the `nums` array. To do this, we must start at the end of the array. We store all these suffix products directly in `nums` array. 

For the last pass, we see a pattern that we can follow to get the resulting product except self array. Let's use an example to visualize this pattern: `nums` = `[1,2,3,4]`. The prefix product array would be `[1,2,6,24]` and the suffix product array would be `[24, 24, 12, 4]`.
```
prefix = [1, 2, 6, 24]
product = [24, 24, 12, 4]
```
<ul>
  <li>For the first element, the product would equate to multiplying all the succeeding elements in the array, which is done on the second element of the suffix product array. Since there is no element before the current one, we can simply set it to `prefix[2]`</li>
  <li>For the second element, the product would equate to multiplying the element before by the product of the elements after, which is done by multiplying the first element of the prefix with the third element of the suffix.</li>
  <li>Same pattern follows for third element, where `i = 2` and product except self = `prefix[i-1] * suffix[i+2]</li>
  <li>For the last element, we rely on the product of all the preceding elements, which is done on the second last element of the prefix product array. Since there is no element after the current one, we can simply set it to this `prefix[n-2]`.</li>
</ul>

We rewrite the `nums` array to be the array of all products except self in order to conserve space. This modification during iteration would not affect the following elements in any way as we are accessing past elements of the other array we created.

Lastly, just to stay aligned with the problem description, we set the `answer` array to the final `nums` array and return `answer`. In Python, this is simply just reference assignment (pointing to same place in memory) so the effects on runtime and memory on this step is negligible. 

**Example Test Cases:**

| Input  | Output |
| ------------- | ------------- |
| <code>nums = [1,2,3,4]</code>  | <code>[24,12,8,6]</code> |
| <code>nums = [-1,1,0,-3,3]</code>  | <code>[0,0,9,0,0]</code> |
| <code>nums = [1,0]</code>  | <code>[0,1]</code> |


**Statistics**: Beat 98% of solutions in runtime and 99% of solutions in memory usage.

<img width="408" alt="image" src="https://github.com/moonscape09/LeetCode/assets/101025804/85e9558a-de01-4580-a278-39284525de2d">
