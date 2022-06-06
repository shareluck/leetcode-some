# 链表相关题目
## 翻转单链表
1. 迭代   pre next cur 
   
    - 记录下一结点
    - 改变当前结点的指向 指向前一结点
    - 更新 前一结点的值 为当前结点
    - 更新 当前结点的值 为记录的下一结点

```js
function todo(head){
    let cur = head ,nex = null ,pre =null
    while(head){
        next = cur.next 
        cur.next = pre 
        pre = cur
        cur = next 
    }
    return pre
}
```
2. 递归
- 终止条件 当前结点 和 当前结点的下一结点 均存在 （head && head.next ）
- 翻转操作 head.next.next = head 当前结点的下一节点的next指针指向当前结点
- 操作完当前结点需要将当前结点的 next 指针 置空 （等于断开）

```js
function todo(head){
    if(!head || !head.next){
        return head 
    }
    let newHead = todo(head.next)
    head.next.next = head
    head.next = null
    return newHead
}
```



