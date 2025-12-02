
Problem Statement: You are given an array and your task is to find the element that appears at least n/3 times in the array.

Difficulty: Medium

Topics: Array, Counting

Constraints: - `1 <= nums.length <= 5 * 10^4`
- `-10^9 <= nums[i] <= 10^9`

Approach: We initialize and maintain two counts and two elements and we iterate through the array if our count 1 decreases to 0 and the current element is not equal to the second initialized element we replace the first initialized element and reset the count same goes for the count and each time we encounter either we increase the respective count and if neither decrease the count of both. After the array iteration we check for the occurrences of the two elements and find the answer from the two.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Counting

---

Code:

class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        int cnt1 = 0, cnt2 = 0, el1 = INT_MIN, el2 = INT_MIN;
        for (int i : nums){
            if (cnt1 == 0 && i != el2){
                el1 = i;
                cnt1 = 1;
            }
            else if (cnt2 == 0 && i != el1){
                el2 = i;
                cnt2 = 1;
            }
            else if (i == el1) cnt1++;
            else if (i == el2) cnt2++;
            else{
                cnt1--;
                cnt2--;
            }
        }
        vector<int> ans;
        cnt1 = 0, cnt2 = 0;
        for (int i : nums){
            if (i == el1) cnt1++;
            if (i == el2) cnt2++;
        }
        int req = (nums.size()/3)+1;
        if (cnt1 >= req) ans.push_back(el1);
        if (cnt2 >= req) ans.push_back(el2);
        return ans;
    }
};