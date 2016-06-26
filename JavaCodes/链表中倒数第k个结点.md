## 链表中倒数第k个结点

### 题目描述
输入一个链表，输出该链表中倒数第k个结点。

### 思路
1. 用两个指针对链表进行遍历，两个指针相隔k个节点，先走的那个指针到走完时，后走的那个指针就指向第k个节点
2. 需要注意的几点
    * 链表可能为空，返回null
    * k值可能为0，返回null
    * 链表的节点可能不够k个返回null

### 代码
    /*
    public class ListNode {
        int val;
        ListNode next = null;
    
        ListNode(int val) {
            this.val = val;
        }
    }*/
    public class Solution {
        public ListNode FindKthToTail(ListNode head,int k) {
    		if (head == null || k == 0) {
    			return null;
    		}
    		
    		ListNode right = head;
    		for (int i = 0; i < k -1; i++) {
    			if (right.next != null) {
    				right = right.next;
    			} else {
    				return null;
    			}
    		}
    		ListNode left = head;
    		while (right.next != null) {
    			left = left.next;
    			right = right.next;
    		}
    		return left;
        }
    }
