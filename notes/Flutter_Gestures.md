---
title: 'Flutter Gestures'
date: '2020-01-02'
type: programing 
---

# Flutter Gestures

Flutter cung cấp  **GestureDetector Widget** để xử lý tất cả các loại [[Gesture]]. Để xác định 1 cử chỉ tác động lên 1 widget chúng ta chỉ cần bọc nó bên trong GestureDetector. 

```flutter
body: Center( 
   child: GestureDetector( 
      onTap: () { 
         _showDialog(context); 
      }, 
      child: Text( 'Hello World', ) 
   ) 
),
```
Một số cử chỉ và các sự kiện tương ứng được đưa ra dưới đây
- Tap
	- onTapDown
	- onTapUp
	- onTap
	- onTapCancel
- Double tap
	- onDoubleTap
	- Long press
	- onLongPress
- Vertical drag
	- onVerticalDragStart
	- onVerticalDragUpdate
	- onVerticalDragEnd
- Horizontal drag
	- onHorizontalDragStart
	- onHorizontalDragUpdate
	- onHorizontalDragEnd
- Pan
	- onPanStart
	- onPanUpdate
	- onPanEnd

## Cơ chế phát hiện cử chỉ cấp thấp
 Flutter cũng cung cấp một cơ chế phát hiện cử chỉ cấp thấp thông qua Listener widget. Nó sẽ phát hiện tất cả các tương tác của người dùng và sau đó gửi các sự kiện sau:
- PointerDownEvent
- PointerMoveEvent
- PointerUpEvent
- PointerCancelEvent


## Một vài cử chỉ khác
Flutter còn cung cấp một số nhỏ các widget để thực hiện các cử chỉ cụ thể đơn giản cũng như phức tạp:
- Dismissible − Hỗ trợ flick gesture để đóng widget.
- Draggable − Hỗ trợ drag gesture để di chuyển widget.
- LongPressDraggable − Hỗ trợ drag gesture để duy chuyển widget, khi widget cha có thể kéo thả
- DragTarget − Chấp nhận Draggable widget
- IgnorePointer − Ẩn widget
- AbsorbPointer − Dừng việc xử lý cử chỉ trên widget
- Scrollable − Hỗ trợ cuộn nội dung trong widget

---
Tags: [[Flutter]]