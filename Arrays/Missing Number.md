
Problem Statement: You are given an array of size n consisting of all the integers in the range [0, n-1] except for one and your task is to find that one integer that is missing.

Difficulty: Easy

Topics: Array, Bit Manipulation, Sorting

Constraints: - `n == nums.length`
- `1 <= n <= 10^4`
- `0 <= nums[i] <= n`
- All the numbers of `nums` are **unique**.

Approach: We take two variables one in which we are calculating the XOR of all the numbers in the range [0, n-1] and one in which we calculate the XOR of all the elements of the array and the resulting number will be the XOR of these two XOR's.

Time Complexity:  O(n) since we need to traverse the array at least once to find the XOR

Space Complexity: O(1) since we need to take just the XOR variables

Pattern Learned: XOR of two same numbers can cancel each other out 


---
if we have an array 1, 2, 3, 4, 5, 6, 8, 9, 10 . Then if we take the XOR then it will be 1^2^3^4^5^6^8^9^10^ and the XOR of all the numbers is 1^2^3^4^5^6^7^8^9^10^
so the XOR of the two XOR's is 1^2^3^4^5^6^8^9^10^1^2^3^4^5^6^7^8^9^10^  we can see that each element has a pair except for 7 so the only element that will remain after the elimination is 7.

---

Code:

class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int sum = 0;
        for (int i=0 ; i<n ; i++){
            sum += nums[i];
        }
        return ((n*(n+1))/2)-sum;
    }
};