
Problem Statement: We are given an array of zeroes and ones and our task is to find the max number of consecutive ones.

Difficulty: Easy

Topics: Array

Constraints: - `1 <= nums.length <= 10^5`
- `nums[i]` is either `0` or `1`.

Approach: We traverse through the array while keeping track of the max consecutive ones till that point and the number of ones till that point if we encounter a 1 we increase the count of ones by 1 and if we encounter a zero we reset the counter to 0 and take the max of the max consecutive and current count and update it in max consecutive and finally return the max consecutive.

Time Complexity: O(n)

Space Complexity:O(1)

Pattern Learned: Max updating on condition

---

Code:

class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int n = nums.size();
        int curr = 0;
        int max_con = 0;
        for (int i=0 ; i<n ; i++){
            if (nums[i] == 1){
                curr++;
                max_con = max(max_con, curr);
            }
            else{
                curr = 0;
            }
        }
        return max_con;
    }
};