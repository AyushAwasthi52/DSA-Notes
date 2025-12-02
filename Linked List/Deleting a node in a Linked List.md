
Problem Statement: You are given the node to be deleted in a linked list and you have to do it without the access to the head.

Difficulty: Easy

Topics: Linked List

Constraints: - The number of the nodes in the given list is in the range `[2, 1000]`.
- `-1000 <= Node.val <= 1000`
- The value of each node in the list is **unique**.
- The `node` to be deleted is **in the list** and is **not a tail** node.

Approach: We change the value of this node to the value of the next node and change its next pointer to the node next to its next.

Time Complexity: O(1)

Space Complexity: O(1)

Pattern Learned: Node deletion

Problem Link: https://leetcode.com/problems/delete-node-in-a-linked-list/description/

---

Code:



/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        ListNode* temp = node->next;
        node->next = node->next->next;
        delete temp;
    }
};