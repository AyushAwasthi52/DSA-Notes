
Problem Statement: You are given an array of integers ad your jib is to find the next lexicographic arrangement of the array.

Difficulty: Medium

Topics: Array, Sorting

Constraints: - `1 <= nums.length <= 100`
- `0 <= nums[i] <= 100`

Approach: Find the first element from the end that is less than the element to its immediate right and then find the first element from the end that is greater than that element and swap the two and then reverse the array to the right of the element that was brought to the middle.

Time Complexity: O(n log n) 

Space Complexity: O(1)

Pattern Learned: Permutation and Lexicographic Order

---

Code:

class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int n = nums.size();
        int ind;
        for (ind=n-2 ; ind>=0 ; ind--){
            if (nums[ind] < nums[ind+1]) break;
        }
        if (ind == -1) sort(nums.begin(), nums.end());
        else{
            for (int i=n-1 ; i>ind ; i--){
                if (nums[i] > nums[ind]){
                    swap(nums[i], nums[ind]);
                    break;
                }
            }
            reverse(nums.begin()+ind+1, nums.end());
        }
    }
};