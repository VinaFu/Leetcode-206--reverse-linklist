# Leetcode-206--reverse-linklist

理解一下指针概念，然后看清往哪里指：
和stack差不多

解法一：
  
                # Definition for singly-linked list.
                # class ListNode:
                #     def __init__(self, val=0, next=None):
                #         self.val = val
                #         self.next = next
                class Solution:
                    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
                        prev = None               //serve as a pointer,start as a none
                        while head != None:
                            cur = head            // head is a value here;cur is the position to add new node, cur's place never change
                            head = head.next      // occupy the next place
                            cur.next = prev       // link the next place
                            prev = cur            // put prev to cur place
                        return prev
                  
                    cur
                     1，  2，  3，  4
             prev   head
                    prev  head

                    def reverse(llist):              // input is llist
                        # Write your code here  
                        prev = None                  // empty 
                        cur=llist                    // equal to input
                        while cur:
                            next = cur.next         // occupy the next position
                            cur.next = prev         // insert a prev
                            prev= cur               // move the cur as the first place
                            cur = next              // link to the next position/ insert complished
                        return prev



解法二 - recursion 
那最后一项当作单独循环项

        class Solution:
            def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
                if not head:
                    return None
                        // 空集返回none

                newHead = head
                if head.next:
                    newHead = self.reverseList(head.next) //等于新输入的值
                    head.next.next = head
                head.next = None

                return newHead

                 #   思路    head  newHead      
                 #   1，  2，  3，  4     null （以3-4为sub-task）
                 #                       head.next  4- null 
                 #             head.next.next 回头到4
                 #             head.next= none 断掉4-null
