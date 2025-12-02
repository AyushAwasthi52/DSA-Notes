
Problem Statement: You are given the head of a linked list and your task is to find the middle node of the linked list without using any extra space.

Difficulty: Easy

Topics: Linked List

Constraints: - The number of nodes in the list is in the range `[1, 100]`.
- `1 <= Node.val <= 100`

Approach: We create two nodes fast and slow and move the slow node normally and the fast node at a speed of two nodes per movement and when the fast node reaches the end the slow node would have traveled exactly halfway through the list

Time Complexity: O(n)

Space Complexity: O(1)

Pattern Learned: Tortoise Hair Method

Problem Link:  https://leetcode.com/problems/middle-of-the-linked-list/description/

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
    ListNode* middleNode(ListNode* head) {
        ListNode* fast = head;
        ListNode* slow = head;
        while (fast && fast->next){
            fast = fast->next->next;
            slow = slow->next;
        }
        return slow;
    }
};