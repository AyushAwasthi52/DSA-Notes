
Problem Statement: A good number is one which has odd numbers at all its odd indices and even numbers at all its even indices and given a number n you have to find the number of good numbers of length n.

Difficulty: Medium

Topics: Math, Recursion

Constraints: - `1 <= n <= 1015`

Approach: Using the law of counting the total no of ways we can get good numbers is by the formula 5 to the power of the number of even positions and 4 to the power of the number of odd positions but using the simple multiplication method takes too much time so we use the same power method as the POW(x, n) question and calculate the answer. 

Time Complexity:  $O(logn)$

Space Complexity: O(1)

Pattern Learned: Recursion

Problem Link:  https://leetcode.com/problems/count-good-numbers/description/

---

Code:
class Solution {
public:
    long long MOD = 1e9+7;
    long long pow(long long x, long long n) {
        if (n == 0) return 1;
        long long a = pow(x, n/2);
        return n % 2 == 0 ? (a * a)%MOD : (a * a * x)%MOD;
    }
    int countGoodNumbers(long long n) {
        long long even = (n+1)/2, odd = n/2;
        return static_cast<int>((pow(5, even)*pow(4, odd)) % MOD);
    }
};

