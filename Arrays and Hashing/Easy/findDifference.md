<h1>Question: <a href="https://leetcode.com/problems/find-the-difference-of-two-arrays/description/">Find The Difference of Two Arrays</a></h1>

```
class Solution {
public:
    vector<vector<int>> findDifference(vector<int>& nums1, vector<int>& nums2) {

        unordered_map<int, int> freq_map1;
        unordered_map<int, int> freq_map2;
        vector<vector<int>> distinct = {{}, {}};

        for (int i = 0; i < nums1.size(); i++) {
            freq_map1[nums1[i]]++;
        }

        for (int i = 0; i < nums2.size(); i++) {
            freq_map2[nums2[i]]++;
        }

        for (int i = 0; i < nums1.size(); i++) {
            if (freq_map1[nums1[i]] > 0 && freq_map2[nums1[i]] == 0) {
                distinct[0].push_back(nums1[i]);
                freq_map1[nums1[i]] = 0;
            } 
        }

        for (int i = 0; i < nums2.size(); i++) {
            if (freq_map1[nums2[i]] == 0 && freq_map2[nums2[i]] > 0) {
                distinct[1].push_back(nums2[i]);
                freq_map2[nums2[i]] = 0;
            }
        }

        return distinct;
    }
};
```

**Data structures/Algorithms used**: Arrays, Hash maps

**Time complexity**: O(n + m) (n = length of parameter array: `nums1`, m = length of parameter array: `nums2`)

**Space complexity**: O(n + m) (n = length of parameter array: `nums1`, m = length of parameter array: `nums2`)

**Time taken**: 15 mins

**Explanation:**
A multi-pass algorithm that first stores the frequency of elements in `nums1` and `nums2` in the frequency maps: `freq_map1` and `freq_map2`, respectively. 

Afterwards, both arrays are iterated seperately, checking for whether it's elements exists in the other array's frequency maps. If not, then that element is added to the corresponding vector in `distinct` (a nested vector). The frequency of that distinct element is then set to 0, so it doesn't get appended again to it's `distinct` array (in the case there are duplicates within the same array).
**Example Test Cases:**


| Input  | Output |
| ------------- | ------------- |
| <code>nums1 = [1,2,3], nums2 = [2,4,6]</code>  | [[1,3],[4,6]] |
| <code>nums1 = [1,2,3,3], nums2 = [1,1,2,2]</code>  | [[3],[]] |
| <code>nums1 = [-68,-80,-19,-94,82,21,-43], nums2 = [-63]</code> | [[-19,82,-68,21,-43,-94,-80],[-63]] |

**Statistics:** Beats 67.07% of solutions in runtime and 11.25% of solutions in memory usage
