# 【LeetCode】002.Add Two Numbers

---

### Description：
You are given two non-empty linked lists representing two non-negative integers.
 
你有两个非空链表代表两个非负整数。

The digits are stored in reverse order and each of their nodes contain a single digit.

数字以相反的顺序存储，它们的每个节点都包含一个数字。

Add the two numbers and return it as a linked list.

这两个数相加返回一个链表。

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

你可以假设这两个数字不包含任何前导零，除了第0个数字本身。

Example:
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```

### 时间复杂度 O(m+n)，空间复杂度 O(1)解决办法：
```
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int carry = 0;
        ListNode result = new ListNode(-1);
        ListNode p3 = result;
        while (l1 != null || l2 != null) {
            if (l1 != null) {
                carry += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                carry += l2.val;
                l2 = l2.next;
            }
            p3.next = new ListNode(carry % 10);
            p3 = p3.next;
            carry /= 10;
        }
        if (carry == 1)
            p3.next = new ListNode(1);
        return result.next;
    }
}
```






