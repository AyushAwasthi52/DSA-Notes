
Problem Statement: You are given an array and you have to return the element that occurs at least n/2 times in the array considering such an element always exists.

Difficulty: Easy

Topics: Array

Constraints: - `n == nums.length`
- `1 <= n <= 5 * 10^4`
- `-10^9 <= nums[i] <= 10^9`

Approach: We start a count and a the first number if the count reaches negative update the element to the current element following that we increase the count by 1 each time we encounter the element and decrease by 1 each time we encounter any other.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Counting

---

Code: 
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int cand = nums[0], cnt = 0;
        for (int i : nums){
            if (cnt == 0) cand = i;
            cnt += (cand == i) ? 1 : -1;
        }
        return cand;
    }
};