
Problem Statement: Given an array return the sum of  sub array with the largest sum

Difficulty: Medium

Topics: Array, Dynamic Programming

Constraints: - `1 <= nums.length <= 10^5`
- `-10^4 <= nums[i] <= 10^4`

Approach: We take two variables current sum and max sum and run across the array once with the following rile update the value of current sum with the max of current number and the sum of the current number and the current sum since it would be pointless to use a sum which is less than the current number and then return the max sum which too was checked at each step with the current sum

Time Complexity: O(n)

Space Complexity: O(1)

Pattern Learned: Kardane's Algorithm which is one of the most general algorithm

---

Code:

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int curr_sum = 0, max_sum = INT_MIN;
        for (int i : nums){
            curr_sum = max(i, curr_sum+i);
            max_sum = max(max_sum, curr_sum);
        }
        return max_sum;
    }
};