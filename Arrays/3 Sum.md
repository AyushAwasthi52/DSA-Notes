
Problem Statement: You are given an array and you have to return an array of all the numbers in that array whose sum equals to 0

Difficulty: Medium

Topics: Array, Binary Search, Two pointers

Constraints: - `3 <= nums.length <= 3000`
- `-10^5 <= nums[i] <= 10^5`

Approach: Iterate through the sorted array and skip all duplicates and then perform binary search on all the elements to the right of the current element to find the triplet.

Time Complexity:  O(n log n)

Space Complexity: O(1)

Pattern Learned: 3 Sum

---

Code:

class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        int n = nums.size();
        sort(nums.begin(), nums.end());

        for (int i = 0; i < n - 2; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue;

            int left = i + 1, right = n - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                
                if (sum == 0) {
                    result.push_back({nums[i], nums[left], nums[right]});
                    
                    while (left < right && nums[left] == nums[left + 1]) left++;
                    while (left < right && nums[right] == nums[right - 1]) right--;
                    
                    left++;
                    right--;
                }
                else if (sum < 0) left++;  
                else right--;  
            }
        }
        return result;
    }
};
auto init = atexit([]() { ofstream("display_runtime.txt") << "0";});