
Problem Statement: You are given an array of numbers in which each index represents the height of a tower and we have to find the two points which can trap the most water if used as a container.

Difficulty: Medium

Topics: Two pointers

Constraints: - `n == height.length`
- `2 <= n <= 105`
- `0 <= height[i] <= 104`

Approach: We take two pointers left and right and move them following the rule that we move the pointer that has less height towards the center until the left is less than the right in index value. 

Time Complexity: O(n)

Space Complexity: O(1)

Pattern Learned: Two Pointers

Problem Link:  https://leetcode.com/problems/container-with-most-water/description/

---

Code:

class Solution {
public:
    int maxArea(vector<int>& height) {
        int n = height.size();
        int left = 0, right = n-1;
        int max_volume = INT_MIN;
        while(left < right){
            int h = min(height[left], height[right]);
            int volume = h*(right-left);
            max_volume = max(max_volume, volume);
            if (height[left] < height[right]) left++;
            else right--;
        }
        return max_volume;
    }
};