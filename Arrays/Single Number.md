
Problem Statement: We are given an array where each element occurs exactly twice except for one element which occurs once we need to find that number.

Difficulty: Easy

Topics: Array, Bit Manipulation

Constraints: **Constraints:**

- `1 <= nums.length <= 3 * 10^4`
- `-3 * 10^4 <= nums[i] <= 3 * 10^4`
- Each element in the array appears twice except for one element which appears only once.

Approach: We traverse the array and find the XOR of all the elements and the answer will be the final XOR of the array since all the elements form a pair and reduce to zero similar to Missing Numbers.

Time Complexity: O(n)

Space Complexity: O(1)

Pattern Learned: Same as Missing Numbers

---

Code:

class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int n = nums.size();
        int x = nums[0];
        for (int i=1 ; i<n ; i++){
            x = x^nums[i];
        }
        return x;
    }
};