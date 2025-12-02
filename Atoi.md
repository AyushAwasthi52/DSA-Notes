Problem Statement: You are given a string and your task is to convert it into integers and return the integer with the following rules:
Implement the `myAtoi(string s)` function, which converts a string to a 32-bit signed integer.

The algorithm for `myAtoi(string s)` is as follows:

1. **White space**: Ignore any leading white space (`" "`).
2. **Signedness**: Determine the sign by checking if the next character is `'-'` or `'+'`, assuming positivity if neither present.
3. **Conversion**: Read the integer by skipping leading zeros until a non-digit character is encountered or the end of the string is reached. If no digits were read, then the result is 0.
4. **Rounding**: If the integer is out of the 32-bit signed integer range `[-231, 231 - 1]`, then round the integer to remain in the range. Specifically, integers less than `-231` should be rounded to `-231`, and integers greater than `231 - 1` should be rounded to `231 - 1`.

Return the integer as the final result.

Difficulty: Medium

Topics: String, Recursion

Constraints: - `0 <= s.length <= 200`
- `s` consists of English letters (lower-case and upper-case), digits (`0-9`), `' '`, `'+'`, `'-'`, and `'.'`.

Approach: We first remove all the leading white spaces from the string and check if a sign is present and if it is we maintain a variable sign for conformation and remove the sign from the string. Next we iterate the string till there are only digits present or the string reaches the end and we create a long long that can store the final number with a check that it does not increase beyond INT_MAX if it does return INT_MAX or INT_MIN immediately as per the sign and if the loop terminates successfully then return the number with its sign.

Time Complexity: O(n)

Space Complexity: O(1)

Pattern Learned: stoi

Problem Link: https://leetcode.com/problems/string-to-integer-atoi/description/

---

Code:

class Solution {
public:
    int myAtoi(string s) {
        unsigned long long ans = 0, n = s.size();
        int i = 0;
        while (i<n && s[i] == ' ') i++;
        bool sign = true;
        if(i<n && s[i] == '-'){
            sign = false;
            i++;
        }
        else if (i<n && s[i] == '+') i++;
        for (; i<n ; i++) {
            if (!isdigit(s[i])) break;
            ans = ans*10 + ((int)s[i]-(int)'0');
            if (ans > INT_MAX) return sign ? INT_MAX : INT_MIN;
        }
        return static_cast<int>(sign ? ans : 0-ans);
    }
};