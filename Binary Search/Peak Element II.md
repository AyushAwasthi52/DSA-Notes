
Problem Statement: You are given a 2-D matrix and your task is to find the element that is the peak that is the element that is greater than all its neighbors.

Difficulty: Medium

Topics: Binary Search on 2-D arrays

Constraints: - `m == mat.length`
- `n == mat[i].length`
- `1 <= m, n <= 500`
- `1 <= mat[i][j] <= 105`
- No two adjacent cells are equal.

Approach: Perform binary search row wise and find the greatest element in the row and with each row use the peak element graph method to move the low and high bound.

Time Complexity:  O(n log m)

Space Complexity: O(1)

Pattern Learned: 2-D Array Binary Search

---

Code:

class Solution {
public:
    vector<int> findPeakGrid(vector<vector<int>>& mat) {
        int n = mat.size();
        int m = mat[0].size();
        int low = 0, high = m-1;
        while (low <= high){
            int mid = low + (high - low) /2;
            int x = 0;
            for (int i = 1 ; i < n ; i++){
                if (mat[i][mid] > mat[x][mid]) {
                    x = i;
                }
            }
            if ((mid > 0 && mat[x][mid] < mat[x][mid-1])) high = mid - 1;
            else if (mid < m-1 && mat[x][mid] < mat[x][mid+1]) low = mid + 1;
            else return {x, mid};
        }
        return {-1, -1};
    }
};
