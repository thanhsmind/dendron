---
type: math
---
# Pointer Arithmetic: Phép toán số học trên con trỏ

C++ cho phép thực hiện các phép tính cộng hoặc trừ  số nguyên trên con trỏ ==(+, -, ++, --)==

Nếu *pointer* trỏ tới 1 số nguyên `var ptr *int ` thì *ptr+1* là ==địa chỉ của số nguyên tiếp theo trong bộ nhớ sau ptr==


==Chú ý: ptr+1 không trả về địa chỉ vùng nhớ sau ptr, ptr+1 trả về địa chỉ vùng nhớ của đối tượng tiếp theo thuộc kiểu mà ptr trỏ tới==

Nếu *pointer* trỏ tới 1 số nguyên ( 4byte hoặc 8 byte) thì *ptr+1* sẽ trỏ tới địa chỉ các 4 bytes hoặc 8 byte so với địa chỉ ban đầu, **ptr+5** nghĩa là cách 5 số nguyên (20 byte, hoặc 40 bytes) sau ptr. 

Ví dụ: sử dụng kiểu int, mỗi địa chỉ trong số này khác nhau 4 byte, nên địa chỉ mỗi lần tăng sẽ nhảy 4 byte. 
```c++

#include <iostream> 
using namespace std; 

int main() { 

	int value = 5; 
	int *ptr = &value; 
	cout << ptr << '\n'; 
	cout << ptr + 1 << '\n'; 
	cout << ptr + 2 << '\n'; 
	cout << ptr + 3 << '\n'; 
	
	system("pause"); 
	
	return 0; 
}
```

Ví dụ: sử dụng kiểu double, mỗi số cách nhau 8 bytes, nên địa chỉ mỗi lần sẽ nhảy lên 8 bytes
```c++

#include <iostream> 
using namespace std; 

int main() { 

	double value = 5; 
	double *ptr = &value; 
	
	cout << ptr << '\n'; 
	cout << ptr + 1 << '\n'; 
	cout << ptr + 2 << '\n'; 
	cout << ptr + 3 << '\n'; 
	
	system("pause"); 
	
	return 0; 
}
```
Nếu *point* trỏ đến một ký tự char( 1byte, ptr+5 sẽ nhảy 5 byte)

