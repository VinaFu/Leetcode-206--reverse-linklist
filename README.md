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
                        //占位下一个可能的点
                      cur.next = prev
                        //接头 = 插向前一个位置
                      prev = cur
                        // prev现在等于cur，见下图。
                      cur = nxt
                        // 站位挪后一个
                  return prev
                        // 返回输入的东西
                  
             Head      
             NULL     1，  2，  3，  4
             prev   cur
                    prev  cur
