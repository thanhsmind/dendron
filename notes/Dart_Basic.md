---
type: programing 
---
# Dart Basic
- Mọi thứ trong Dart đều là Object, và có các hàm tiện ích đi kèm.
- ==Tránh sử dụng dynamic type== dynamic type làm cho chương trình tiềm ẩn lỗi không fix được.
## Classes
```dart
class Product{
 	var name="Macbook pro";
	var _price = 2000.99;
}
```
- private variable: `_variable-name` được hiểu là biến private
- các biến còn lại là public variable
## `final` vs `const`
`final` và `const` là các keyword tạo ra các biến fix valued. 
`const`: fix ngay từ compile-time
`final`:  có thể assign value trong thời gian chạy
```dart
	int calculateSquare(int value){
	  return value * value;
	}

	void main() {
	  const double PI = 3.1415;
	  final int square_7 = calculateSquare(7);

	  print(PI);
	  print(square_7);
	}
```

## Kiểu dữ liệu cấu trúc trong Dart
### List
Giống loại dữ liệu Array của các ngôn ngữ lập trình khác. Có 2 loại : 
- Fixed List: Số phần từ chứa trong List được cố định
	```dart
	List<int> aFixedList = new List(8);
	aFixedList.add(1);
	# aFixedList chỉ chứa tối đa 8 element
	```
- Growable Lists: Số lượng element được chứa trong List có thể tăng
	```dart
	List<String> aGrowableList = new List();
	aGrowableList.add("shark");
	aGrowableList.add("Tomato");
	
	// Change a value at an existing index in a list
	aGrowableList[0]= "Apple";
	```

### Map
Giống kiểu dữ liệu Dictionary trong [[Python]]. Map là 1 tập hợp của _key-value_. Sừ dụng _Map class_ để khởi tạo 1 map. 2 thông số quan trọng của map là _Type of Key_, _Type of Value_
```dart
var trainCompartments = new Map<int, String>();
trainCompartments[1] = "ENgine";
trainCompartments[2] = "WOmen chair car";
trainCompartments[3] = "Men chair car";

print("Variable: $trainCompartments");

```

