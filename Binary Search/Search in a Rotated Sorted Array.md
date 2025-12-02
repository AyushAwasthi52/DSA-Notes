
Problem Statement: Given an array of sorted elements rotated by x places search for the given element in log n time complexity

Difficulty: Medium

Topics: Binary Search

Constraints: 1 <= nums.length <= 5000
-10^4 <= nums[i] <= 10^4
All values of nums are unique.
nums is an ascending array that is possibly rotated.
-10^4 <= target <= 10^4

Approach: At each mid element check whether the right or the left is a sorted part and solve accordingly

Time Complexity: O(log n) 

Space Complexity: O(1)

Pattern Learned: Binary Search

---

Code:

class Solution {
public:
    int search(vector<int>& nums, int target) {
        int n = nums.size();
        int left = 0, right = n-1;
        while(left <= right){
            int mid = left + (right-left)/2;
            if (nums[mid] == target) return mid;
            if (nums[left] <= nums[mid]){
                if (nums[left] <= target && nums[mid] > target){
                    right = mid-1;
                }
                else{
                    left = mid+1;
                }
            }
            else{
                if (nums[mid] < target && nums[right] >= target){
                    left = mid+1;
                }
                else{
                    right = mid-1;
                }
            }
        }
        return -1;
    }
};