
Problem Statement: You are given a string and you have to find the sum of beauty of all the sub strings given that beauty of a sub string is the difference of the minimum and maximum frequency in that array.

Difficulty: Medium

Topics: Hash Table, Strings, Counting

Constraints: - `1 <= s.length <= 500`
- `s` consists of only lowercase English letters.

Approach: We move in two loops where the outer loop moves from 0 to n-1 and the inner loop from i+1 to n-1 covering all the sub strings in that we can use a hash map to count the frequency while maintaining a minimum and maximum frequency at all times and adding the difference to our answer at all the steps.

Time Complexity:  O(n^2)

Space Complexity: O(1)

Pattern Learned: Hash Map

Problem Link:  https://leetcode.com/problems/sum-of-beauty-of-all-substrings/description/

---

Code:

class Solution {
public:
    int beautySum(string s) {
        int n = s.size();
        int ans = 0;

        for (int i = 0; i < n; i++) {
            vector<int> freq(26, 0);
            for (int j = i; j < n; j++) {
                freq[s[j] - 'a']++;

                int mx = 0, mn = INT_MAX;
                for (int f : freq) {
                    if (f > 0) {
                        mx = max(mx, f);
                        mn = min(mn, f);
                    }
                }
                ans += mx - mn;
            }
        }
        return ans;
    }
};