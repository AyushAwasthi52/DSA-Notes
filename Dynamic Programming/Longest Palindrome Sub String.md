
Problem Statement: You are given a string s and your task is to find the longest sub string that can be found in the string that is a palindrome

Difficulty: Medium

Topics: Two Pointers, String, Dynamic Programming

Constraints: - `1 <= s.length <= 1000`
- `s` consist of only digits and English letters.

Approach: 
Brute Force => We independently check all the possible sub strings and find the answer.
Dynamic Programming => To improve upon the brute force we can just make a table and check whether when we are checking between two points the string inside excluding the edge characters is a palindrome and then check if the edge characters are equal and then proceed as follows.
Expand Around the Center => We take a general idea that the palindromic sub strings generally move around the center meaning that we can easily confirm what the length of a sub string is if we take a character as a center and move to its left and right while checking the palindrome quality with two cases whether it itself is a part of a even palindrome or the center of a odd sub string.


Time Complexity: O(n^2)

Space Complexity: O(1)

Pattern Learned: Expand around the center

Problem Link: https://leetcode.com/problems/longest-palindromic-substring/

---

Code:

class Solution {
public:
    string longestPalindrome(string s) {
        int n = s.size();
        int max_length = 0;
        string pall = {s[0]};
        for (int i=0 ; i<n ; i++) {
            if (i<n-1 && s[i]==s[i+1]) {
                int left = i-1, right=i+2;
                while (left >=0 && right <= n-1 && s[left] == s[right]) {
                    left--;
                    right++;
                }
                int len = right-left-1;
                if (len > max_length) {
                    max_length = len;
                    pall = s.substr(left+1, len);
                }
            }
            if (i>0 && i<n-1 && s[i-1] == s[i+1]) {
                int left = i-1, right = i+1;
                while (left >=0 && right <= n-1 && s[left] == s[right]) {
                    left--;
                    right++;
                }
                int len = right-left-1;
                if (len > max_length) {
                    max_length = len;
                    pall = s.substr(left+1, len);
                }
            }
        }
        return pall;
    }
};