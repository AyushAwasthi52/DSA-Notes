
Problem Statement: In a sorted array of elements where each element appears twice find the only element that appears once.

Difficulty: Medium

Topics: Binary Search, Counting

Constraints: - `1 <= nums.length <= 10^5`
- `0 <= nums[i] <= 10^5`

Approach: Consider the even and odd positioning of the elements in the array while applying binary search

Time Complexity:  O( log n)

Space Complexity: O(1)

Pattern Learned: Binary Search

---

Code:

class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int n = nums.size();
        int left = 0, right = n-1;
        while (left <= right){
            int mid = left + (right-left)/2;
            int a = (mid > 0) ? nums[mid-1] : -1, b = (mid < n-1) ? nums[mid+1] : -1;
            if (a != nums[mid] && b != nums[mid]) return nums[mid];
            if (a == nums[mid]){
                if (mid%2 == 0) right = mid-1;
                else left = mid+1;
            }
            else{
                if (mid%2 != 0) right = mid-1;
                else left = mid+1;
            }
        }
        return -1;
    }
};