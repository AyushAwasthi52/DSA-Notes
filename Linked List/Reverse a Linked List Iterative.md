
Problem Statement: You are given the head of a linked list and your task is to reverse it using a loop in place.

Difficulty: Easy

Topics: Reversing a linked list

Constraints: - The number of nodes in the list is the range `[0, 5000]`.
- `-5000 <= Node.val <= 5000`

Approach: We take three variables previous, current and next. We assign the value of a null pointer to the previous and head to current and next and run the loop till current is not null and do the following in order we assign the value of next of current to next and then we assign the value previous to the next of next and then we assign current as previous and finally update current as next.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Reversing a linked list

Problem Link:  https://leetcode.com/problems/reverse-linked-list/submissions/1666148319/

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
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* current = head;
        ListNode* next = head;
        while (current){
            next = current->next;
            current->next = prev;
            prev = current;
            current = next;
        }
        return prev;
    }
};