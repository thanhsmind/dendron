---
title: 'Flutter Basic'
date: '2020-01-02'
type: programing 
---

# Flutter Basics	

- [[Flutter Câu lệnh thường dùng Flutter - Flutter Commands]]
- [[Flutter Những tools cần thiết khi cài Flutter ( flutter doctor)]]
- [[Flutter Project Structure]]


## Khái niệm căn bản trong Flutter
### Widgets
Trong Flutter mọi thứ đều là [[Flutter Widgets]]. Mỗi ứng dụng flutter là 1 widget ( Root widget) nó bao gồm một hoặc nhiều các widget con. Mỗi widget con có thể bao gồm 1 hoặc nhiều widget con khác.
![Flutter Structure App](flutter-structure-app.png)

### Layout
Trong Flutter, các [[Flutter Layout]] cũng là 1 loại widget. Nhiệm vụ của người lập trình là sử dụng các widget này bố trí vị trí hiển thị của nó để tạo lên các layout khác nhau.

### Gestures
[[Flutter Gestures]] là 1 tiện ích không hiển thị trên giao diện nhưng có khả năng nắm bắt các thao tác của người dùng như : Nhấp, kéo, vuốt, chạm. 

### State
Flutter widgets quản lý các  [[State]] thông qua một widget đặc biệt là [[statefullwidget]] . Tất cả các Widget cần [[statefullwidget]] để quản lý các trạng thái(state) và kết nối với các widget khác. Flutter widget là 1 dạng reactive ([[Reactive Programming]]) . [[statefullwidget]] sẽ tự động thay đổi giao diện hiển thị khi thay đổi trạng thái. Khi nó thay đổi, sẽ tôí ưu chỉ thay đổi những thành phần liên quan, không thay đổi toàn bộ, chỉ vẽ lại những chỗ cần thiết nên sẽ hiệu quả hơn.

### Layers
[[Flutter Architectural layers Flutter framework]] các thành phần sẽ được nhóm lại theo mức độ phức tạp và được sắp xếp rõ ràng theo các tầng có độ phức tạp giảm dần. 
![Architechtural layers Flutter](flutter-archdiagram.png)


---
Tags: [[Flutter]]