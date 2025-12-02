
Problem Statement: You are given the heads of two linked lists and you have to return the intersection point of the two if present null otherwise.

Difficulty: Easy

Topics: Linked List

Constraints: - The number of nodes of `listA` is in the `m`.
- The number of nodes of `listB` is in the `n`.
- `1 <= m, n <= 3 * 104`
- `1 <= Node.val <= 105`
- `0 <= skipA <= m`
- `0 <= skipB <= n`
- `intersectVal` is `0` if `listA` and `listB` do not intersect.
- `intersectVal == listA[skipA] == listB[skipB]` if `listA` and `listB` intersect.

Approach: We take a two pointer approach where we just make the two pointers to point to the heads and if we reach the same point then it is intersection if either reaches the end first we move it to the start of the second and null in other cases.

Time Complexity:  O(n+m)

Space Complexity: O(1)

Pattern Learned: Two Pointers

Problem Link:  https://leetcode.com/problems/intersection-of-two-linked-lists/description/

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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* temp1 = headA, *temp2 = headB;
        while (temp1 || temp2) {
            if (temp1 == temp2) return temp1;
            if (!temp1) temp1 = headB, temp2 = temp2->next;
            else if (!temp2) temp2 = headA, temp1 = temp1->next;
            else temp1 = temp1->next, temp2 = temp2->next;
        }
        return nullptr;
    }
};