# 链表
- [x] [83. 删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
       ListNode current = head;
       while(current!=null&& current.next!=null){
           if(current.val==current.next.val){
               current.next = current.next.next;
           }else{
               current = current.next;
           }
       }
        return head;

    }
}
```
- [x] [82. 删除排序链表中的重复元素 II](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/)

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode p,q; //p指向前一个结点，q指向后一个结点
        ListNode ans = new ListNode(-1,head); //构造假头结点，next指向真头结点，方便条件判断
        p = ans; //p首先指向假头结点
        q = head; //q首先指向真正的头结点
        while(q!=null&&q.next!=null){ //如果q非空并且q.next也非空进入循环
            if(p.next.val==q.next.val){//如果p和q的next指向的值相等进入二层循环
                while(q.next!=null&&p.next.val==q.next.val)//当值相等时，q指针后移直到q.next指向的值不等于p.next.val时
                    q = q.next;               
                q = q.next;//跳出二层循环后，这时q指针后移，丢弃所有重复的结点
                p.next = q;//把现在的p和q连接起来
            }else{//如果p和q的next指向的值不相等
                p = q;//p指针后移
                q = q.next;//q指针后移
            }
        }
        return ans.next;//丢弃假头结点返回真头结点
    }
}
```
- [x] [反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        /****第一次尝试*****/
        if(head==null||head.next==null) return head; //当没有结点或结点只有一个的情况直接返回
        ListNode p,c,r; //创建三个结点
        p = head; //p：pre指向头结点
        c = head.next; //c：current指向头结点后一个结点，第一行进行判断证明布置一个结点
        p.next = null;//头结点指向null
        if(c.next!=null) //当前结点的下一个结点不为空
            while(c.next!=null){ //进入循环
                r = c.next; //r:rear 用r暂存当前结点的下一个结点
                c.next = p; //当前结点反转指针
                p = c; //pre后移
                c = r; //current后移
            }
        c.next = p;//将最后一个结点的指针反转
        return c;
        /*******第二次进行了优化**********/
        if(head==null||head.next==null) return head;
        ListNode p,c,r;
        p = null;
        c = head;
        while(c!=null){
            r = c.next;
            c.next = p;
            p = c;
            c = r;
        }
        return p;
        /*****第三次尝试递归调用*******/
        if(head==null||head.next==null) return head;
        ListNode current = reverseList(head.next);//一直递归到上一行返回的最后一个结点
        //此时head是原链表的倒数第二个结点
        head.next.next = head;
        //此时head是原链表的第一个结点
        head.next = null;
        return current;
    }
}
```
- [x] [反转链表ii](https://leetcode-cn.com/problems/reverse-linked-list-ii/)
- [x] [合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)
- [x] [分割链表](https://leetcode-cn.com/problems/partition-list/)
- [x] [排序链表](https://leetcode-cn.com/problems/sort-list/)
- [x] [重排链表](https://leetcode-cn.com/problems/reorder-list/)
- [x] [判断链表是否有环](https://leetcode-cn.com/problems/linked-list-cycle/)
- [x] [循环链表的环入口ii](https://leetcode-cn.com/problems/linked-list-cycle-ii/)
- [x] [回文链表](https://leetcode-cn.com/problems/palindrome-linked-list/)
- [x] [链表深克隆](https://leetcode-cn.com/problems/copy-list-with-random-pointer/)

