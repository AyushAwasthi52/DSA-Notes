
Problem Statement: You are given an array and a number k you have to return the number of sub-arrays that have sum equal k.

Difficulty: Medium

Topics: Array, Hash-Map

Constraints: - `1 <= nums.length <= 2 * 10^4`
- `-1000 <= nums[i] <= 1000`
- `-10^7 <= k <= 10^7`

Approach: Make a map of two integers where the key is the number and the value is the number of sub-array that have the sum equal to key and iterate the array with sum being the sum of all the elements till that point. If at any point the sum-k is already present in the map then add its count to the current count and at every step record the value of the current sum in the map.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Math

---

Code: 

class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int n = nums.size();
        unordered_map<int,int> mp;
        mp[0] = 1;
        int sum = 0, cnt = 0;
        for (int i : nums){
            sum += i;

            if (mp.find(sum-k) != mp.end()){
                cnt += mp[sum-k];
            }

            mp[sum]++;
        }

        return cnt;
    }
};

