
Problem Statement: You are given an array and a target you have to return the indices of the two elements such that there sum equals the target.

Difficulty: Easy

Topics: Array, Hash Table

Constraints: - `2 <= nums.length <= 10^4`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`
- **Only one valid answer exists.**

Approach: Make a Unordered hash map and store the indices of all the elements in that and then traverse the array and look for the complement of the current element (complement of the current element is the target - current element ) and if it exists in the map return the two indices.

Time Complexity: O(n)

Space Complexity: O(n)

Pattern Learned: Hash Maps


---

Code: 

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        unordered_map<int, int> mp;
        for (int i=0 ; i<n ; i++) mp[nums[i]] = i;
        for (int i=0 ; i<n ; i++){
            if (mp.find((target - nums[i])) != mp.end() && mp[(target - nums[i])] != i) return {i,mp[(target - nums[i])]};
        }
        return {-1, -1};
    }
};