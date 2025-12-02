
Problem Statement: You are given a 2 D matrix and your task is to search for a element in the matrix in efficient time given that each row is sorted from left to right and each column is sorted from top to bottom

Difficulty: Medium

Topics: Binary Search

Constraints: - `m == matrix.length`
- `n == matrix[i].length`
- `1 <= n, m <= 300`
- `-10^9 <= matrix[i][j] <= 10^9`
- All the integers in each row are **sorted** in ascending order.
- All the integers in each column are **sorted** in ascending order.
- `-10^9 <= target <= 10^9`

Approach: Start iterating from the first row and last column if the element we need is larger than the current element move down the matrix and if the element is smaller than the current element move back a column

Time Complexity:  O(log m* n)

Space Complexity: O(1)

Pattern Learned: Search in a 2-D Matrix

---

Code:

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int m = matrix.size(), n = matrix[0].size();

        int i = 0, j = n-1;

        while (i < m && j >= 0){
            if (matrix[i][j] == target) return true;

            if (matrix[i][j] < target) i++;

            else j--;
        }

        return false;
    }
};