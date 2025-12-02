
Problem Statement: We are a house robber and we are supposed to rob houses each with a specific amount of money as per the array given to us our task is to find the maximum amount of money considering that we cannot rob any two adjacent houses.

Difficulty: Medium

Topics: Dynamic Programming

Constraints: - `1 <= nums.length <= 100`
- `0 <= nums[i] <= 400`

Approach:
Basic => We can use recursion approach for the pick not pick approach and return the max money when we reach the value n.
Better => We can maintain an array that we can use to signify the maximum loot that the robber can get till that point and use that to find the loot in the following boxes where with each box the loot is the maximum of the sum of the loot in that house with the max loot till the house one house before and the loot in the house just before the house with the sole exception where the second house loot is the maximum of the loot in the first and second house.
Best => We can just eliminate the need of the table since what we need is just the previous two elements that we can maintain using the climbing stairs method.

Time Complexity: O(n)

Space Complexity: O(1)

Pattern Learned: Fibonacci Sequence

Problem Link: https://leetcode.com/problems/house-robber/description/

---

Code:
class Solution {
public:
    int rob(vector<int>& nums) {
        int n = nums.size();
        if (n == 1) return nums[0];
        int a = nums[0], b = max(nums[0], nums[1]);
        for (int i=3 ; i<=n ; i++) {
            int temp = max(nums[i-1]+a, b);
            a = b;
            b = temp;
        }
        return b;
    }
};
