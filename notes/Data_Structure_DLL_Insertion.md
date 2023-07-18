---
type: math
---
# Data Structure DLL Insertion

Có 4 cách để thêm 1 node vào trong DLL
1. Thêm vào đầu danh sách DLL
2. Thêm vào sau 1 node cụ thể cho trước
3. Thêm vào cuối danh sách DLL
4. Thêm vào trước 1 node cụ thể cho trước

### Thêm vào đầu danh sách DLL
5 bước để thêm 1 node vào đầu danh sách. 
![[DLL_add_front1.png]]
```java
// Adding a node at the front of the list
public void push(int new_data)
{
    /* 1. allocate node
    * 2. put in the data */
    Node new_Node = new Node(new_data);
 
    /* 3. Make next of new node as head and previous as NULL */
    new_Node.next = head;
    new_Node.prev = null;
 
    /* 4. change prev of head node to new node */
    if (head != null)
        head.prev = new_Node;
 
    /* 5. move the head to point to the new node */
    head = new_Node;
}
```
### Thêm vào sau 1 node cụ thể cho trước
7 bước để thêm 1 node vào sau 1 node xác định
![[DLL_add_middle1.png]]
```java

/* Given a node as prev_node, insert a new node after the given node */
public void InsertAfter(Node prev_Node, int new_data)
{
 
    /*1. check if the given prev_node is NULL */
    if (prev_Node == null) {
        System.out.println("The given previous node cannot be NULL ");
        return;
    }
 
    /* 2. allocate node
    * 3. put in the data */
    Node new_node = new Node(new_data);
 
    /* 4. Make next of new node as next of prev_node */
    new_node.next = prev_Node.next;
 
    /* 5. Make the next of prev_node as new_node */
    prev_Node.next = new_node;
 
    /* 6. Make prev_node as previous of new_node */
    new_node.prev = prev_Node;
 
    /* 7. Change previous of new_node's next node */
    if (new_node.next != null)
        new_node.next.prev = new_node;
}
```
### Thêm vào cuối danh sách DLL
7 bước cần thực hiện khi thêm 1 node mới vào cuối danh sách
![[DLL_add_end1.png]]
```java
// Add a node at the end of the list
void append(int new_data)
{
    /* 1. allocate node
     * 2. put in the data */
    Node new_node = new Node(new_data);
 
    Node last = head; /* used in step 5*/
 
    /* 3. This new node is going to be the last node, so
     * make next of it as NULL*/
    new_node.next = null;
 
    /* 4. If the Linked List is empty, then make the new
     * node as head */
    if (head == null) {
        new_node.prev = null;
        head = new_node;
        return;
    }
 
    /* 5. Else traverse till the last node */
    while (last.next != null)
        last = last.next;
 
    /* 6. Change the next of last node */
    last.next = new_node;
 
    /* 7. Make last node as previous of new node */
    new_node.prev = last;
}
```
### Thêm vào trước 1 node cụ thể cho trước
8 bước cần thực hiện : 
1. Kiểm tra nếu **next_node** là Null hay Not Null. Nếu là Null thì return về vì 1 new node không thể được add vào trước 1 NULL
2. Khởi tạo New node
3. Set data cho new_node
4. Set prev_node cho new_node là previous node của next_node. new_node->prev= next_node->prev.
5. Set previous pointer của next_node là new_node. next_node->prev=new_node
6. Set next pointer của new_node là next_node, new_node->next = next_node.
7. Nếu previous node của new_node không phải là NULL, thì set next pointer của previous node là new_node, new_node->prev->next = new_node
8. Trái lại, nếu prev của new_node là NULL, thì nó sẽ là new head node. *head_ref = new_node
![[DLL-add-given-node.png]]
```java
# insertion before a given node
 
# A linked list node
class Node:
    def __init__(self, x):
        self.data = x
        self.prev = None
        self.next = None
 
# /* Given a reference (pointer to pointer)
# to the head of a list
# and an int, inserts a new node on
# the front of the list. */
def push(head_ref, new_data):
 
    # /* 1. allocate node */
    new_node = Node(new_data)
 
    # /* 2. put in the data */
    new_node.data = new_data
 
    # /* 3. Make next of new node as
    # head and previous as None */
    new_node.next = head_ref
    new_node.prev = None
 
    # /* 4. change prev of head node to new node */
    if (head_ref != None):
        head_ref.prev = new_node
 
    # /* 5. move the head to point to the new node */
    head_ref = new_node
 
    return head_ref
 
# /* Given a node as next_node, insert
# a new node before the given node */
 
 
def insertBefore(head_ref, next_node, new_data):
 
    # /*1. check if the given next_node is NULL */
    if (next_node == None):
        print("the given next node cannot be NULL")
        return
 
    # /* 3. put in the data */
    new_node = Node(new_data)
 
    # /* 4. Make prev of new node as prev of next_node */
    new_node.prev = next_node.prev
 
    # /* 5. Make the prev of next_node as new_node */
    next_node.prev = new_node
 
    # /* 6. Make next_node as next of new_node */
    new_node.next = next_node
 
    # /* 7. Change next of new_node's previous node */
    if (new_node.prev != None):
        new_node.prev.next = new_node
 
    # /* 8. If the prev of new_node is NULL, it will be
    #   the new head node */
    else:
        head_ref = new_node
 
    return head_ref
 
# This function prints contents of linked
# list starting from the given node
def printList(node):
    last = None
    print("Traversal in forward direction ")
    while (node != None):
        print(node.data, end=" ")
        last = node
        node = node.next
 
    print("\nTraversal in reverse direction ")
    while (last != None):
        print(last.data, end=" ")
        last = last.prev
 
 
# /* Driver program to test above functions*/
if __name__ == '__main__':
 
    # /* Start with the empty list */
    head = None
    head = push(head, 7)
 
    head = push(head, 1)
 
    head = push(head, 4)
 
    # Insert 8, before 1. So linked list becomes 4.8.1.7.NULL
    head = insertBefore(head, head.next, 8)
 
    print("Created DLL is: ")
    printList(head)
 
# This code is contributed by mohit kumar 29
```

---
Tags: [[Algorithms]] -  [[Data Structure]]
Reference:
Related: 