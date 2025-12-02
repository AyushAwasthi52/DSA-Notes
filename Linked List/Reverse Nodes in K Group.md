
Problem Statement: You are given the head of a linked list an integer k you have to rotate the nodes of the linked list in groups of k

Difficulty: Hard

Topics: Linked List, Recursion

Constraints: - The number of nodes in the list is `n`.
- `1 <= k <= n <= 5000`
- `0 <= Node.val <= 1000`

Approach: We create two functions one to find the k node from the current node and one to reverse the linked list as normal and then we create a pointer to the previous node in that list. Then we need to move through the list and at each step we find the k node from the current node if it is null we just make the prev point to the current temp and return the value. If the k node is not null we store the next node in a var and we make it so that the current list is a separate list by making the k node point to null and reverse it. Now we make sure to update the list such that the next of previous is the k node and the then the prev becomes  the head and the next iteration starts from the next. 

Time Complexity:  O(n)

Space Complexity: O(1)

Pattern Learned: Grouping of linked list

Problem Link:  https://leetcode.com/problems/reverse-nodes-in-k-group/description/

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
    ListNode* kthNode(ListNode* head, int k) {
        ListNode* temp = head;
        k--;
        while (k && temp) {
            temp = temp->next;
            k--;
        }
        return temp;
    }
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
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* temp = head;
        ListNode* prev = nullptr;
        while (temp) {
            ListNode* kth = kthNode(temp, k);
            if (!kth) {
                if (prev) prev->next = temp;
                break;
            }
            ListNode* next = kth->next;
            kth->next = nullptr;
            reverseList(temp);
            if (temp == head) head = kth;
            else prev->next = kth;
            prev = temp;
            temp = next;
        }
        return head;
    }
};