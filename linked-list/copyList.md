


## 复制复杂链表
- 不止是只有next 和 value 的链表结构 
1. 迭代 + 结点拆分
    - 遍历链表 复制当前结点（cur -> curCopy）
    - 确定 curCopy 的位置 curCopy.next = cur.next  cur.next = curCopy 
    - 再次遍历 链表 将 其他的属性 （除了val,next 以外）copy 基础值 直接复制 ，引用值 需要指向    copy 结点
    - 对扩展的 链表 进行拆分 拆除原链表 与 copy 链表 return  copy链表

eg：
```js
//结点的构造函数
function ListNode(val,next ,random){
    this.next = next 
    this.val = val
    this.random = random  //举指针例子 random 
}
//复制操作函数 
function todo(head){
    let cur = head ,res
    if(!head){
        return head
    }
    while(cur){
        //新增一个curCopy
        const newListNode = new ListNode(cur.val,cur.next,null)
        cur.next = newListNode 
        cur = cur.next.next 
    }
    // 重置一下 cur
    cur = head
    while(cur){
        //获取 curCopy
        const curCopy = cur.next 
        //复制random 注意指向的是 cur.random.next （即 cur random 指向的结点的copy结点）            
        curCopy.random = cur.random ? cur.random.next :null
        cur = cur.next.next 
    }
    // 重置一下 cur
    cur = head
    res = head.next 
    while(cur && cur.next){
        const curCopy = cur.next 
        cur.next = cur.next.next 
        curCopy.next = curCopy.next ? curCopy.next.next : null
        cur = cur.next 
    }
    return res 
}
```