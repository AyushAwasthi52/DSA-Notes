
Problem Statement: Peak element is the element which is greater than both its left and right neighbor return the index of one such element in the given array. 

Difficulty: Medium

Topics: Binary Search

Constraints: - `1 <= nums.length <= 1000`
- `-2^31 <= nums[i] <= 2^31 - 1`
- `nums[i] != nums[i + 1]` for all valid `i`.

Approach: Think of the distribution like a graph and use that graph to determine whether the peak lies in the left or the right half

Time Complexity: O(log n)

Space Complexity: O(1)

Pattern Learned: Graph representation

---

Code:

class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        int n = nums.size();
        int left = 0, right = nums.size()-1;
        while (left <= right){
            int mid = left + (right-left)/2;
            long long a = mid > 0 ? nums[mid-1]:LLONG_MIN, b = mid<n-1 ? nums[mid+1]:LLONG_MIN;
            if (a < nums[mid] && b < nums[mid]) return mid;
            if (a < nums[mid]) left = mid+1;
            else right = mid-1;
        }
        return -1;
    }
};