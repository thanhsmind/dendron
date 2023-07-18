---
title: 'Reactive Programming'
date: '2020-01-02'
type: programing
---

# Reactive Programming

==Reactive programming is programming with asynchronous data streams==

Khi thực hiện 1 task thường quan tâm tới 3 yếu tố
- Gía trị được trả về từ task
- Thông báo lỗi (nếu có)
- Thời điểm task hoàn thành

**Stream** dùng đề truyền tải dữ liệu, nó phát ra (emit) 3 thứ: 
- value
- error
- completed ( tín hiện khi kết thúc 1 task) theo 1 trình tự thời gian từ nơi phát ra (producer) tới nơi lắng nghe ( subcribler).

## Đặc điểm chính của Reactive Programming
==RX = OBSERVABLE + OBSERVER + SCHEDULERS==
- **Observable**: Là nơi cung cấp, chứa dữ liệu, nó sẽ xử lý dữ liệu và cung cấp cho các component khác lắng nghe nó. Observable có thể phát ra bất kỳ số lượng item nào, hoặc nó có thể kết thúc với 1 message thành công hay 1 error
- **Observers**: là nơi sẽ nhận dữ liệu đầu vào và xử lý nó theo 1 mục đích cụ thể. Để nhận được dữ liệu từ Observable, Observer sẽ đăng ký (subcribe) bằng phương thức subcribeOn(). Khi đó, khi Observable phát ra dữ liệu, các Observers sẽ nhận được dữ liệu trong onNext() callback. Nếu có 1 error được throw ra từ Observable thì Observer đăng ký sẽ nhận được lỗi trong onError().
- **Schedulers**:  Reactive Programming là lập trình bất đồng bộ ([[asynchronous]]) nên người lập trình phải quản lý được các thread xử lý. Reactive Programming cung cấp Scheduler là thành phần để cho Observable & Observer biết được nên chạy trên thread nào. Thường hàm observeOn() dùng để giao tiếp với các Observers, scheduleOn() dùng để giao tiếp với các Observable. 



Example:
```php
$source = \Rx\Observable::fromArray([1, 2, 3, 4]);

$source->subscribe(
    function ($x) {
        echo 'Next: ', $x, PHP_EOL;
    },
    function (Exception $ex) {
        echo 'Error: ', $ex->getMessage(), PHP_EOL;
    },
    function () {
        echo 'Completed', PHP_EOL;
    }
);

//Next: 1
//Next: 2
//Next: 3
//Next: 4
//Completed
```

```java
//Observable. This will emit the data
Observable<String> database = Observable
                .just(new String[]{"1", "2", "3", "4"});    //Operator
				
Observer<String> observer = new Observer<String>() {
   @Override
	public void onCompleted() {
		//...
	}

	@Override
	public void onError(Throwable e) {
		//...
	}

	@Override
	public void onNext(String s) {
		//...
	}
};


database.subscribeOn(Schedulers.newThread())          //Observable runs on new background thread.
        .observeOn(AndroidSchedulers.mainThread())    //Observer will run on main UI thread.
        .subscribe(observer);                         //Subscribe the observer

```
## Lợi ích của Reactive programming

- Cho phép chuyển từ stream này qua stream khác, merge nhiều stream thành 1 stream mới mà không làm thay đổi trạng thái của stream ban đầu.
- Làm cho ứng dụng chạy nhanh hơn, phản hồi nhanh hơn. Giảm lưu trữ, quản lý các state trung gian. 
- Giúp xử lý lỗi trong lập trình bất đồng bộ ([[asynchronous]]) dễ dàng hơn. Reactive Programming giúp tách biệt xử lý lỗi với logic. Giúp code rõ ràng hơn. 

![[merge-thread-reactive-programming.png]]


---
Tags: [[Programing]]