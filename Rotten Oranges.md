
Problem Statement: You are given a grid of numbers 0 1  2 and 1 represents a fresh orange and 2 represents a rotten orange and 0 an empty cell. In 1 unit of time a rotten orange can rot all surrounding fresh oranges directly attached. Return the time taken before all the oranges are rotten or -1 if not possible.

Difficulty: Medium

Topics: Graph, BFS

Constraints: - `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 10`
- `grid[i][j]` is `0`, `1`, or `2`.

Approach: We can store all the rotten orange indices at the start in a queue and start BFS but this time we do the BFS n times where n is the number of elements in the queue at the start of each while iteration and then if we have replaces at least one orange with rotten orange then we increase the time by 1 with each while iteration

Time Complexity: O(n*m)

Space Complexity: O(n*m)

Pattern Learned: Multi Source BFS

	Problem Link: https://leetcode.com/problems/rotting-oranges/description/

---

Code:

class Solution {
public:
    bool isSafe(int x, int y, int n, int m) {
        return x >= 0 && y >= 0 && x < n && y < m;
    }

    int orangesRotting(vector<vector<int>>& grid) {
        int n = grid.size(), m = grid[0].size();
        queue<pair<int,int>> q;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (grid[i][j] == 2) {
                    q.push({i, j});
                }
            }
        }

        vector<vector<int>> directions = {{0,1},{1,0},{0,-1},{-1,0}};
        int time = 0;

        while (!q.empty()) {
            int sz = q.size();
            bool spread = false;

            while (sz--) {
                auto [x, y] = q.front(); q.pop();

                for (auto &d : directions) {
                    int nx = x + d[0], ny = y + d[1];
                    if (isSafe(nx, ny, n, m) && grid[nx][ny] == 1) {
                        grid[nx][ny] = 2;
                        q.push({nx, ny});
                        spread = true;
                    }
                }
            }

            if (spread) time++;
        }

        for (auto &row : grid)
            for (int cell : row)
                if (cell == 1) return -1;

        return time;
    }
};
