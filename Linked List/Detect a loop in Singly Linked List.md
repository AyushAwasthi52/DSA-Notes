
Problem Statement: You are given a linked list and you have to return true if it contains a loop and false if it doesn't.

Difficulty: Medium

Topics: Linked List

Constraints: - The number of the nodes in the list is in the range `[0, 104]`.
- `-105 <= Node.val <= 105`
- `pos` is `-1` or a **valid index** in the linked-list.

Approach: We use the tortoise hare method and exit the loop if the fast or the next of fast is null and return false otherwise there is a loop somewhere and our fast pointer will come back in the middle and meet the slow pointer at some point of time.

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Loop Detection

Problem Link:  https://leetcode.com/problems/linked-list-cycle/description/

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
    bool hasCycle(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast && fast->next){
            fast = fast->next->next;
            slow = slow->next;
            if (fast == slow) return true;
        }
        return false;
    }
};