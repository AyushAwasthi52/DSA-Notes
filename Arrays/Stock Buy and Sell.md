
Problem Statement: You are given an array where each element represents the price of a stock on day i and your task is to find the maximum profit that can be made if you were to buy and sell the stock considering that you cannot sell before buying.

Difficulty: Easy

Topics: Array, Dynamic Programming

Constraints: - `1 <= prices.length <= 10^5`
- `0 <= prices[i] <= 10^4`

Approach: Just take two variables but and profit set buy to the first element and start iterating through the array with the second element as soon as you encounter any element that is of less cost than the element at first pointer position change the first element pointer and at each step update the profit to the max value

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Dynamic Algorithm

---

Code:

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        int curr_max = prices[n-1];
        int max_profit = 0;
        for (int i=n-2 ; i>=0 ; i--){
            max_profit = max(max_profit, curr_max - prices[i]);
            curr_max = max(curr_max, prices[i]);
        }
        return max_profit;
    }
};