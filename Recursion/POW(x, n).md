
Problem Statement: We are given a double x and a number n and we have to return the value of x to the power of n

Difficulty: Medium

Topics: Math, Recursion

Constraints: - `-100.0 < x < 100.0`
- `-231 <= n <= 231-1`
- `n` is an integer.
- Either `x` is not zero or `n > 0`.
- `-104 <= xn <= 104`

Approach: The naive solution would be to multiply the number x n times to itself to get the desired result but that could be optimized through recursion.

Here we can create a function that return 1 if n == 0 and we break the problem into two cases first that n is even when we can just create the function again with x and n/2 and since n/2+n/2 = n pow(x,n/2)*pow(x,n/2) = pow(x, n) and similarly for the case of odd numbers we just need to need to multiply an extra x for the missing 1 in the case.

Time Complexity:  $O(logn)$

Space Complexity: $O(1)$

Pattern Learned: Recursion

Problem Link:  https://leetcode.com/problems/powx-n/description/

---

Code:


class Solution {
public:
    double pow(double x, long long n) {
        if (n == 0) return 1;
        double a = pow(x, n/2);
        return n % 2 == 0 ? a * a : a * a * x;
    }
    double myPow(double x, int n) {
        long long N = n;
        if (n < 0) {
            N = abs(static_cast<long long>(n));
            x = 1/x;
        }
        return pow(x, N);
    }
};