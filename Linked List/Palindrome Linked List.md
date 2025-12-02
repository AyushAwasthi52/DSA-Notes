
Problem Statement: You are given a linked list and you have to check if it forms a palindromic array.

Difficulty: Easy

Topics: Reversing a linked list, Palindromes

Constraints: - The number of nodes in the list is in the range `[1, 105]`.
- `0 <= Node.val <= 9`

Approach: We find the middle of the linked list and reverse the list from that point and then we check for the values moving from both the head and the new found end of the list

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Reversing

Problem Link: https://leetcode.com/problems/palindrome-linked-list/description/

---

Code:

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverse(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while (curr != nullptr) {
            ListNode* next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
    
    bool isPalindrome(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast != nullptr && fast->next != nullptr) {
            slow = slow->next;
            fast = fast->next->next;
        }
        ListNode* rev = reverse(slow);
        while (rev != nullptr) {
            if (head->val != rev->val) {
                return false;
            }
            head = head->next;
            rev = rev->next;
        }
        return true;
    }
};+