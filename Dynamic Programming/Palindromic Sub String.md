
Problem Statement: You are given a string and your task is to find the total number of sub strings that are palindromic.

Difficulty: Medium

Topics: Two Pointers, Strings, Dynamic Programming

Constraints: - `1 <= s.length <= 1000`
- `s` consists of lowercase English letters.

Approach: 
Dynamic Programming => You have to create a 2-D array that will hold value true if the string from i to j is palindrome and false otherwise and then check if a string is palindromic by comparing the characters at the position of i and j and the inner string.
Expand Around Center => We can run a loop where each iteration we try to expand the string till it is palindromic considering both even and odd length palindrome possibilities.

Time Complexity:  O(n^2)

Space Complexity: O(1)

Pattern Learned: Expand Around The Center

Problem Link:  https://leetcode.com/problems/palindromic-substrings/description/

---

Code:

class Solution {
public:
    int countSubstrings(string s) {
        int n = s.size();
        int count = 0;
        for (int i = 0 ; i<n ; i++) {
            count++;
            if (s[i] == s[i+1]) {
                count++;
                int left = i-1, right = i+2;
                while (left >=0 && right <= n-1 && s[left] == s[right]) {
                    count++, left--, right++;
                }
            }
            int left=i-1, right=i+1;
            while (left >= 0 && right <= n-1 && s[left] == s[right]) {
                count++, left--, right++;
            }
        }
        return count;
    }
};