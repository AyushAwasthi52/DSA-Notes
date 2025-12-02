
Problem Statement: You are given an array and your task is to return all the quadruplets whose sum is equal to the target.

Difficulty: Hard

Topics: Array, Sorting

Constraints: - `1 <= nums.length <= 200`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`

Approach: Similar to the three sum problem with and additional loop to get the fourth element.

Time Complexity: O( n^2 * log n) 

Space Complexity: O(1)

Pattern Learned: 4 Sum

---

Code:

class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        int n = nums.size();
        sort(nums.begin(), nums.end());
        vector<vector<int>> ans;
        for (int i=0 ; i<n ; i++){
            if (i > 0 && nums[i]==nums[i-1]) continue;
            for(int j=i+1 ; j<n ; j++){
                if (j > i+1 && nums[j] == nums[j-1]) continue;
                int left = j+1, right = n-1;
                long long sum1 = nums[i]+nums[j];
                while(left < right){
                    long long sum = sum1+nums[left]+nums[right];
                    if (sum == target){
                        ans.push_back({nums[i], nums[j], nums[left], nums[right]});
                        while (left < right && nums[left] == nums[left+1]) left++;
                        while (left < right && nums[right] == nums[right-1]) right--;
                        left++;
                        right--;
                    }
                    else if (sum < target) left++;
                    else right--;
                }
            }
        }
        return ans;
    }
};