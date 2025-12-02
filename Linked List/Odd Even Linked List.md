
Problem Statement: You are given a linked list and you have to group together all the even and odd indices. 

Difficulty: Medium

Topics: Linked List

Constraints: - The number of nodes in the linked list is in the range `[0, 104]`.
- `-106 <= Node.val <= 106`

Approach: We take two pointers odd and even where odd points to the head and even points to the next of head and then make it so that the pointers move and updates the next of all nodes to the next of next nodes and finally attach the tail of odd to the head of even.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Grouping in a linked list

Problem Link:  https://leetcode.com/problems/odd-even-linked-list/description/

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
    ListNode* oddEvenList(ListNode* head) {
        if (!head) return head;
        ListNode *evenhead = head->next;
        ListNode *odd = head, *even = head->next;
        while (odd->next && even->next) {
            odd->next = odd->next->next;
            even->next = even->next->next;
            odd = odd->next;
            even = even->next;
        }
        odd->next = evenhead;
        return head;
    }
};