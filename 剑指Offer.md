# 栈与队列

![image-20230321224330035](https://cdn.jsdelivr.net/gh/yzk656/image/202303212243133.png)

![image-20230321225818509](https://cdn.jsdelivr.net/gh/yzk656/image/202303212258545.png)

![image-20230321231826319](https://cdn.jsdelivr.net/gh/yzk656/image/202303212318364.png)

## [剑指 Offer 09. 用两个栈实现队列](https://leetcode.cn/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

> 用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
>
>  
>
> 示例 1：
>
> 输入：
> ["CQueue","appendTail","deleteHead","deleteHead","deleteHead"]
> [[],[3],[],[],[]]
> 输出：[null,null,3,-1,-1]
> 示例 2：
>
> 输入：
> ["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
> [[],[],[5],[2],[],[]]
> 输出：[null,-1,null,null,5,2]
> 提示：
>
> 1 <= values <= 10000
> 最多会对 appendTail、deleteHead 进行 10000 次调用
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class CQueue {
    Deque<Integer> inDeque;
    Deque<Integer> outDeque;
    public CQueue() {
        inDeque=new ArrayDeque();
        outDeque=new ArrayDeque();
    }
    
    public void appendTail(int value) {
        inDeque.offerLast(value);
        while(!inDeque.isEmpty()) {
            outDeque.offerLast(inDeque.pollFirst());
        }
    }
    
    public int deleteHead() {
        if(outDeque.isEmpty()){
            return -1;
        }else{
            return outDeque.pollFirst();
        }
    }
}

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue obj = new CQueue();
 * obj.appendTail(value);
 * int param_2 = obj.deleteHead();
 */
```

掌握知识：

1. 学会使用Deque，是通过ArrayDeque实现
2. 对于Deque，删除头：pollFirst；添加尾：offerLast

## [剑指 Offer 30. 包含min函数的栈](https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof/)

> 定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。
>
>  
>
> 示例:
>
> MinStack minStack = new MinStack();
> minStack.push(-2);
> minStack.push(0);
> minStack.push(-3);
> minStack.min();   --> 返回 -3.
> minStack.pop();
> minStack.top();      --> 返回 0.
> minStack.min();   --> 返回 -2.
>
>
> 提示：
>
> 各函数的调用总次数不超过 20000 次
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class MinStack {
    Deque<Integer> d1;
    Deque<Integer> temp;
    int min;
    /** initialize your data structure here. */
    public MinStack() {
        d1=new ArrayDeque<>();
        temp=new ArrayDeque<>();
        temp.push(Integer.MAX_VALUE);
    }
    
    public void push(int x) {
        d1.push(x);
        temp.push(Math.min(x,temp.peek()));
    }
    
    public void pop() {
        temp.pop();
        d1.pop();
    }
    
    public int top() {
        return d1.peek();
    }
    
    public int min() {
        return temp.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.min();
 */
```

掌握知识：

1. Deque既可以使用队列的方法：offerLast、pollFirst；也可以使用栈的方法：push、poll、peek
2. 通过辅助栈，实现对于每一层，都有对应的最小值存储在辅助栈中
3. 出现了一次：由于有可能删除最小值，因此不能与遇到的最小值比较（`min=Math.min(x,min);`）,要与当前层的最小值进行比较`temp.push(Math.min(x,temp.peek()));`

# 链表

## [剑指 Offer 24. 反转链表](https://leetcode.cn/problems/fan-zhuan-lian-biao-lcof/)

> 定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。
>
>  
>
> 示例:
>
> 输入: 1->2->3->4->5->NULL
> 输出: 5->4->3->2->1->NULL
>
>
> 限制：
>
> 0 <= 节点个数 <= 5000
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/fan-zhuan-lian-biao-lcof
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

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
        ListNode prev=null;
        ListNode cur=head;
        while(cur!=null){
            ListNode next=cur.next;
            cur.next=prev;
            prev=cur;
            cur=next;
        }
        return prev;
    }
}
```

掌握知识：

1. 翻转只需要后一个指向前一个，一次只需要设置一个前置节点；不需要删除A-》B，只需要建立A《=B
2. 进行移动

	        ListNode next=cur.next;
	        cur.next=prev;
	        prev=cur;
	        cur=next;

## [剑指 Offer 35. 复杂链表的复制](https://leetcode.cn/problems/fu-za-lian-biao-de-fu-zhi-lcof/)

> 请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。
>
>  
>
> 示例 1：
>
> 
>
> 输入：head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
> 输出：[[7,null],[13,0],[11,4],[10,2],[1,0]]
> 示例 2：
>
> 
>
> 输入：head = [[1,1],[2,1]]
> 输出：[[1,1],[2,1]]
> 示例 3：
>
> 
>
> 输入：head = [[3,null],[3,0],[3,null]]
> 输出：[[3,null],[3,0],[3,null]]
> 示例 4：
>
> 输入：head = []
> 输出：[]
> 解释：给定的链表为空（空指针），因此返回 null。
>
>
> 提示：
>
> -10000 <= Node.val <= 10000
> Node.random 为空（null）或指向链表中的节点。
> 节点数目不超过 1000 。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/fu-za-lian-biao-de-fu-zhi-lcof
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/
class Solution {
    HashMap<Node,Node> hashmap=new HashMap<>();
    public Node copyRandomList(Node head) {
        if(head==null)
            return null;
        if(!hashmap.containsKey(head)){
            Node temp=new Node(head.val);
            hashmap.put(head,temp);
            temp.next=copyRandomList(head.next);
            temp.random=copyRandomList(head.random);
        }
        return hashmap.get(head);
    }
}
```

掌握知识：

1. 递归，使用哈希表记录每个节点的新的节点的指针