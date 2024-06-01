<h1>Question: https://leetcode.com/problems/two-sum/</h1>

 ```
using namespace std;

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> num_map;
        vector<int> answer;

        for (int i = 0; i < nums.size(); i ++) {
            if (num_map.count(target - nums[i])) {
                answer = {num_map[target - nums[i]], i};
                break;
            } else {
                num_map[nums[i]] = i;
            }
        }

        return answer;
    }
};
 ```

 **Data structures used**: Map

 **Time complexity**: O(n)

 **Space complexity**: O(n)

 <h3>Function</h3>
 Returns the indices of the two elements that add up to the <code>target</code>.


 **Parameters:**
 - <code>nums</code>: array of numbers
 - <code>target</code>: target number

 **Variables:**
 - <code>num_map</code>: a map storing the indices of each number in the nums array.
 - <code>answer</code>: an array that will store the indices of the numbers adding up to the target.


 **Explanation:**
 In this single pass solution, a map is created which the elements of the <code>nums</code> array is stored as keys and the corresponding
 index is stored as the value.

Within the same pass, a check for the existence of the complement of the current iterable to add up to the target is done. If it exists, this means the complement was a preceding element in the array
and hence the answer array stores this complement as the first element and the current iterable as the second. At this point, the loop is broken to reach the `return` statement
at the end.

 **Example Test Cases:**


 | Input  | Output |
 | ------------- | ------------- |
 | <code>nums=[2,7,11,15], target = 9</code>  | [0, 1] |
 | <code>nums=[3,2,4], target = 6</code>  | [1, 2] |
 | <code>nums=[3,3] target = 6</code> | [0, 1] |
