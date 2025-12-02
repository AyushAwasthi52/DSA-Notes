
Problem Statement: We can climb stairs in two ways from a step wither a single step or a double step given a staircase of n steps find the number of ways to reach the top of the staircase.

Difficulty: Easy

Topics: Dynamic Programming 

Constraints: - `1 <= n <= 45`

Approach: Basic => Use recursion to find the number of ways to reach the top stair simulating all the possibilities.
Better => Use an array with each index giving the number of stairs then the value of each index being the number of ways to reach that step which is the sum of the last two indexes since it can be reached through the step before and the step before the before forming something like a Fibonacci sequence.
Best => Instead of wasting space on a continuous array we use two variables to signify the previous two steps since those are the only relevant steps so we do not use the array and maintain the sum and return the value of second element.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Fibonacci Sequence

---

Code:

class Solution {
public:
    int climbStairs(int n) {
        int a = 2, b = 3;
        if (n <= 3) return n;
        int ans;
        for (int i=3 ; i<n ; i++){
            ans = a + b;
            a = b;
            b = ans;
        }
        return b;
    }
};