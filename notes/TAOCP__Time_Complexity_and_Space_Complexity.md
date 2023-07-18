---
type: math
---
# Time Complexity & Space complexity



### Độ phức tạp của thuật toán - Big-O  Notation
Là 1 biểu thức mô tả hành vi của thuật toán ( thời gian tính toán hoặc lượng bộ nhớ cần dùng) khi kích thước dữ liệu đầu vào thay đổi.
***Big-O  Notation*** mô tả mối liên hệ giữa số lượng phần tử đầu vào và số lượng operation - thời gian chạy, lượng bộ nhớ mà thuật toán cần sử dụng. 

![[Big-O-Notation.jpg]]

Ví dụ : 
- Với thuật toán có độ phức tạp  là O(n):  
	- dữ liệu đầu vào có 10 phần tử =>  chương trình phải chạy 10 operation. 
	- dữ liệu đầu vào có 20 phần tử =>  chương trình phải chạy 20 operation. 
- Độ phức tạp O(n²): khi lượng dữ liệu đầu vào tăng gấp đôi => số lượng câu lệnh tăng gấp **2_²_ tức là gấp 4 lần**

Big-O Notation có thể dùng mô tả cho thời gian chạy hoặc số lượng bộ nhớ mà thuật toán cần để sử dụng. 
***[[TAOCP  Time Complexity]]**: Độ phức tạp thời gian là độ phức tạp tính toán mô tả lượng thời gian mà máy tính cần để chạy 1 thuật toán. 
***[[Space complexity]]***: Số lượng bộ nhớ thêm mà thuật toán cần, dựa theo số lượng đầu vào. 

Bài toán Two Sum:
```
Cho 1 mảng gồm N số không trùng nhau. Hãy tìm 2 số trong mảng có tổng bằng X
```

Bài này có thể giải bằng cách: 
- **Cách 1**: Dùng 2 vòng lặp, lặp qua toàn bộ các phần tử của mảng để lấy các cặp. Cách này không tốn thêm bộ nhớ, nhưng **time complexity** O(n²), vì chạy 2 vòng lặp lồng nhau, mỗi vòng lặp có n phần từ.
- **Cách 2**: Duyệt từng phần tử, lưu các phần tử đã duyệt vào 1 set. Mỗi khi gặp 1 phần tử có giá trị A, ta tính B = X-A, rồi kiểm tra xem trong set có B hay không?
 	- Cách này loop 1 lần trong n phần từ đầu vào => **time complexity** O(n)
 	- Cần có 1 biến lưu danh sách các phần tử đã chạy qua => **space complexity** là O(n). 


![[common-data-structure-operations.jpg]]
![[array-sorting-algorithms.png]]
[bigocheatsheet.com](http://bigocheatsheet.com/)

https://toidicodedao.com/2020/12/01/cau-truc-du-lieu-co-ban-p1-big-o-do-phuc-tap/
https://viblo.asia/p/ky-hieu-big-o-su-dung-toan-hoc-de-do-luong-hieu-qua-thuat-toan-oOVlYWkvK8W
https://medium.com/@yenbao1340/time-complexity-%C4%91%E1%BB%99-ph%E1%BB%A9c-t%E1%BA%A1p-c%E1%BB%A7a-thu%E1%BA%ADt-to%C3%A1n-d4d1102ae29f
https://hoclaptrinh.vn/tutorial/cau-truc-du-lieu-amp-giai-thuat-55-bai/giai-thuat-la-gi
https://www.mygreatlearning.com/blog/why-is-time-complexity-essential/#:~:text=Time%20complexity%20is%20the%20amount,of%20code%20in%20an%20algorithm.


---
Tags: [[Algorithms]] - [[TAOCP]]
Reference:
Related: 