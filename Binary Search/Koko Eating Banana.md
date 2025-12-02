
Problem Statement: Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.

Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile. If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer k such that she can eat all the bananas within h hours.


Difficulty: Medium

Topics: Binary Search

Constraints: - `1 <= piles.length <= 104`
- `piles.length <= h <= 109`
- `1 <= piles[i] <= 109`

Approach: While applying the binary search take the number of banana in consideration.

Time Complexity: O(log n)

Space Complexity: O(1)

Pattern Learned: Binary search on answers

---

Code:

class Solution {
public:
    int minEatingSpeed(vector<int>& piles, int h) {
        int n = piles.size();
        sort(piles.begin(), piles.end());
        int left = 1, right = piles[n-1], ans = piles[n-1];
        while (left <= right){
            int mid = left +(right-left)/2;
            long long t = 0;
            for (int i=0 ; i<n ; i++){
                t += (piles[i]+mid-1)/mid;
            }
            if (t <= h){
                ans = mid;
                right = mid-1;
            }
            else left = mid+1;
        }
        return ans;
    }
};