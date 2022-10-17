# Leetcode-206--reverse-linklist

理解一下指针概念，然后看清往哪里指：
和stack差不多

解法一：
  
       class Solution:
              def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
                  prev = None
                  cur = head
                      // 最开始的头是没有，第一个为cur
                  while cur:
                      // 如果cur存在，进行下面的loop。
                      nxt = cur.next
                        //占位下一个可能的点,找好退路位置
                      cur.next = prev
                        //接头 
                      prev = cur
                        // prev现在等于cur，见下图。鸠占鹊巢
                      cur = nxt
                        // 站位挪后一个，鹊往后移动
                  return prev
                        // 返回输入的东西，看看鸠
                  
             Head      
             NULL     1，  2，  3，  4
             prev   cur
                    prev  cur


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
