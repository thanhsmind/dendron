---
type: programing 
---
# DevOps Config Logrotate
### Cách hoạt động của Logrotate
Logrotate được chạy bằng cron. Thường trong Centos script chạy logrotate được đặt trong thư mục cron: 
- `/etc/cron.daily/logrotate`: 1 ngày chạy 1 lần
- `/etc/cron.hourly/logrotate`: 1 hour chạy 1 lần.

### File cấu hình Logrotate
Thư mục  config Logrotate được đặt trong thư mục `/etc/logrotate.d`. Các file config nên được tách riêng ra thành từ file nhỏ, mỗi file nhỏ nên config 1 loại riêng biệt. Khi cập nhật file config xong không cần restart lại Logrotate, do Logrotate chạy bằng cron. 
![[logrotate-config-folder.png]]

### Ý nghĩa các cấu hình

- **Số phiên bản rotate**
	`rotate 4` duy trì 4 phiên bản rotate	
- **Chu kỳ rotate**
	```
	hourly	# 1 hour chạy 1 lần
	daily   # 1 ngày chạy 1 lần
	weekly  # 1 tuần chạy 1 lần
	monthly # 1 tháng chạy 1 lần
	yearly	# 1 năm chạy 1 lần
	```
- **Size**
	Sử dụng `size` để chỉ định kích thước của file log.
	```
		size 100k
		size 100M
		size 100G
	```
- **Compression**
	- **compress**: Cấu hình Logrotate sẽ nén file log lại khi tới chu kỳ rotate
	- **nocompress**: Không nén file log sau khi tới chu kỳ rotate
	- **delaycompress**: command này sẽ delay lại việc nén file log vào lần rotate sau. Cấu hình này đi cùng với `compress` mới có tác dụng.
- **Postrotate**
	Logrotate sẽ chạy script sau khi rotate file log. Thường là các script restart lại ứng dụng sau khi rotate để app switch qua file log mới.
	Ex:
	```
		# restart httpd 
		postrotate
			/usr/sbin/apachectl restart > /dev/null
		endscript 
	```
	`>/dev/null` command này báo với hệ thống là sẽ không export output ra ngoài log.
- **Sharedscript**
	Thông thường `postrotate` script sẽ chạy khi rotate 1 log. Việc này đúng với nhiều files log chạy cùng 1 file cofig logrotate. 
	Ví dụ: Webserver  block 2 files access, và error log. Khi chạy `postrotate` script chạy nó sẽ chạy 2 lần, dẫn tới webserver sẽ bị restart 2 lần. Khi có cấu hình `sharedscript` logrotate sẽ kiểm tra xem nếu có 1 hay hơn 1 log được rotate thì sẽ chạy `postscript` ==1 lần==. Nếu không có log nào được rotate thì `postscript` sẽ không chạy.
	
	### Cách force Test Config Logrotate
	` logrotate --force $CONFIG_FILE`


### Ví dụ một vài config Log cho App
#### Setup Logrotate cho Apache
Logrotate sẽ chạy 1 hour/1 lần. Kiểm tra nếu file log có kích thước trên 100M sẽ rotate. Rotate thành 3 bản. file log mới sẽ đươc tạo với user root, và quyền 0644.
```
# /etc/logrotate.d/httpd  
/var/log/httpd/\*log {  
	hourly  
	size 100M  
	dateext  
	dateformat -%Y%m%d-%s  
	missingok  
	rotate 3  
	create 0644 root root  
	notifempty  
	sharedscripts  
	compress  
	postrotate  
	systemctl reload httpd > /dev/null 2 > /dev/null || true  
	endscript  
}
```

#### Setup Logrotate cho Exim
```
# /etc/logrotate.d/exim
/var/log/exim/\*log {  
	hourly  
	dateext  
	dateformat -%Y%m%d-%s  
	su root root  
	rotate 4  
	missingok  
	notifempty  
	compress  
}
```

#### Setup Logrotate cho Drupal Watchdog
```
# /etc/logrotate.d/drupal_watchdog
/var/log/drupal\_watchdog/\*.log {  
	hourly  
	size 100M  
	dateext  
	dateformat -%Y%m%d-%s  
	missingok  
	rotate 3  
	create 0644 bocvac apage  
	sharedscripts  
	postrotate  
	/bin/kill -HUP \`cat /var/run/syslogd.pid 2> /dev/null\` 2> /dev/null || true  
	/bin/kill -HUP \`cat /var/run/rsyslogd.pid 2> /dev/null\` 2> /dev/null || true  
	endscript  
}
```
	
#### Setup Logrotate cho php
```
/var/log/php/\*log {  
	hourly  
	size 100M  
	dateext  
	dateformat -%Y%m%d-%s  
	missingok  
	rotate 3  
	compress  
	create 0666 root root  
}
```


---
Tags: [[DevOps]] [[Linux]]
