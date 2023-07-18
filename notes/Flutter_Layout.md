---
title: 'Flutter Layout'
date: '2020-01-02'
type: programing 
---

# Flutter Layout
Có 2 loại widget layout chính trong Flutter:
- Single Child widget
- Multiple Child Widgets

## Single Child widget
Các widget này thường có tác dụng điều chỉnh vị trí cho các widget con. 
1 số loại widgets thường dùng của loại này là :
- Center widget: Sử dụng để căn giữa widget con
- Container widget: cung cấp khả năng linh hoạt trong việc đặt widget con bên trong thông qua padding, margin, border.
- Padding widget: Sử dụng để padding widget con. (EdgeInsets class)
- Align widget: căn lề cho widget con sử dụng thuộc tính alignment. 
- FittedBox
- AspectRatio
- ConstrainedBox
- Baseline
- FractinallySizedBox
- IntrinsicHeight
- IntrinsicWidth
- LiimitedBox
- OffStage
- OverflowBox
- SizedBox
- SizedOverflowBox
- Transform
- CustomSingleChildLayout

## Multiple Child Widgets
Widget loại này có khả năng chứa nhiều con bên trong. 
- Row: cho phép bố trí các widget con theo chiều ngang thành 1 hàng
- Column: cho phép bố trí các widget con theo chiều dọc thành 1 cột
- ListView 
- GridView 
- Expanded 
- Table 
- Flow 
- Stack 

---
Tags: [[Flutter]]