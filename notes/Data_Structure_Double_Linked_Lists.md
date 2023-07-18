---
type: math
---
# Data Structure Double Linked Lists(DLL) - Danh sách liên kết kép

Danh sách liên kết đôi là một trường hợp khác của danh sách liên kết ([[Linked List]]). Các hoạt động duyệt qua các node sẽ có thể thực hiện được 2 chiều: về trước và về sau. 
- **Node**: Mỗi Node của Danh sách liên kết kép có thể lưu trữ 1 dữ liệu và được gọi là 1 phần tử.
- **Next**: Mỗi link có thể chứa 1 link tới Next Link, được gọi là next
- **Prev**: Mỗi link có thể chứa 1 link tới Previous Link được gọi là Prev
- **First và Last**: 
![[doubly-linked-list.png]]

### Ưu điểm của Double Linked Lists (DLL) so với [[Linked List]]:
- DLL có thể duyệt 2, chiều xuôi và ngược 
- Xóa trong DLL hiệu quả hơn nếu con trỏ đến node cần xóa được cung cấp. Trong [[Linked List]], để delete 1 node, con trỏ previous node cần thiết. Để lấy được con trỏ previous node thì cần phải duyệt lại danh sách liên kết. Trong DLL, có sẵn previous node.
- Dễ dàng insert 1 node trước 1 node cho trước. 

### Nhược điểm
- Thêm space để lưu trữ previous pointer.
- Tất cả các tác vụ tương tác với DLL thì đều đòi hỏi thêm tương tác với previous pointer. Ví dụ: Thêm phần tử vào danh sách liên kết, thì cần thao tác chỉnh sửa trên previous pointers cùng với next pointers. 

## Các thao tác với DLL
- [[Data Structure DLL Insertion]]
- [[DLL delete]]



https://www.geeksforgeeks.org/delete-a-node-in-a-doubly-linked-list/
https://www.geeksforgeeks.org/doubly-linked-list/
https://www.geeksforgeeks.org/delete-doubly-linked-list-node-given-position/

---
Tags: [[Algorithms]] -  [[Data Structure]]
Reference:
Related: 