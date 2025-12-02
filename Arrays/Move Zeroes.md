
Problem Statement: You are given an array and your task is to move all the zeroes to the end of the array without changing the relative order of the other elements.

Difficulty: Easy

Topics: Array, Two Pointers

Constraints: - `1 <= nums.length <= 10^4`
- `-231 <= nums[i] <= 231 - 1`

Approach: The straightforward solution is to use two pointers example left and right where left is the pointer that moves continuously and right always moves ahead of left whenever left encounters a zero the right moves ahead to find the first element that is not a zero and then swaps the two values.

Time Complexity: O(n) since we move once in the entire array

Space Complexity: O(1) no extra contiguous memory allocated

Pattern Learned: Application of two-pointer in an array

---

Code:

class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int left = 0;

        for (int right = 0; right < nums.size(); right++) {
            if (nums[right] != 0) {
                swap(nums[left], nums[right]);
                left++;
            }
        }
    }
};