2. Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

 ```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        num1, num2 = self.get_number(l1), self.get_number(l2)
        sum_num = num1 + num2

        if sum_num == 0:
            return ListNode()

        res = ListNode(-1)
        curr = res
        
        while sum_num != 0:
            curr.next = ListNode(sum_num % 10)
            curr = curr.next
            sum_num //= 10
        
        return res.next

    def get_number(self, l: Optional[ListNode]) -> int:
        num, digit = 0, 1
        while l:
            num += l.val * digit
            l = l.next
            digit *= 10
        
        return num 
 ```