
Problem Statement: You are given the connected list of a graph and your task is to find the total number of isolated parts of the graph

Difficulty: Medium

Topics: DFS, BFS, Union, Graph

Constraints: - `1 <= n <= 200`
- `n == isConnected.length`
- `n == isConnected[i].length`
- `isConnected[i][j]` is `1` or `0`.
- `isConnected[i][i] == 1`
- `isConnected[i][j] == isConnected[j][i]`

Approach: We can use DFS to traverse the list and every time we find any element for the first time while traversing the outer list we increment the number of provinces by 1 and repeat the same for all the following for all the other nodes.

Time Complexity: O(n * m) 

Space Complexity: O(n)

Pattern Learned: DFS, BFS

Problem Link:  https://leetcode.com/problems/number-of-provinces/description/

---

Code:

class Solution {
public:
    void dfs(int node, int n, vector<vector<int>>& isConnected, vector<bool>& visited) {
        visited[node] = true;
        for (int i=0 ; i<n ; i++) {
            if (isConnected[node][i] && !visited[i]) {
                dfs(i, n, isConnected, visited);
            }
        }
    }

    int findCircleNum(vector<vector<int>>& isConnected) {
        int n = isConnected.size();
        int provinces = 0;
        vector<bool> visited(n, false);
        for (int i=0 ; i<n ; i++) {
            if (!visited[i]) {
                provinces++;
                dfs(i, n, isConnected, visited);
            }
        }
        return provinces;
    }
};