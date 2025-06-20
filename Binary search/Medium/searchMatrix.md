<h1>Question: <a href="https://leetcode.com/problems/search-a-2d-matrix/description/">Search Matrix</a></h1>

```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {

        int left = 0;
        int right = matrix.size() - 1;

        int n = matrix[0].size() - 1;
        int mid;
        while (left <= right) {
            mid = left + (right - left) / 2;
            if (matrix[mid][0] > target) right = mid - 1;
            else if (matrix[mid][n] < target) left = mid + 1;
            else break;
        }
        
        left = 0;
        right = n;
        while (left <= right) {
            int newMid = left + (right - left) / 2;
            if (matrix[mid][newMid] < target) left = newMid + 1;
            else if (matrix[mid][newMid] > target) right = newMid - 1;
            else return true;
        }

        return false;
    }
};
```

**Data structures/Algorithms used**: Binary search

**Time complexity**: O(log(m * n)) (m = number of rows, n = number of columns)

**Space complexity**: O(1)

**Time taken**: 15 mins

**Explanation:**
A multi-binary search algorithm, that first searches for the row with the appropriate intervals (between row[0] and row[row.size() - 1]) that the `target` could be within. 

Once this row is found, then binary search is done again to look for the `target` in this 1D vector. If found, `true` is returned. If not, once the loop is done, `false` is returned.
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]] target = 3</code>  | true |
| <code>matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]] target = 13</code>  | false |


**Statistics:** Beats 100% of solutions in runtime and 75.86% of solutions in memory usage

![image](https://github.com/user-attachments/assets/f1478eb6-5588-4fc0-8150-f38a4f2d94f0)

