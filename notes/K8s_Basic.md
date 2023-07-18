---
type: devops
---

# K8s Basic

## Những thành phần cơ bản
### Pods
- Pods là đơn vị nhỏ nhất mà k8s quản lý. 
- Pod bọc ngoài _container_ và cung cấp 1 số tiện ích health check container
- Thường 1 pod quản lý 1 container
- Mỗi pod thường gắn theo 1 IP address
- Khi pod lỗi, k8s sẽ tắt, loại bỏ pod này, và recreate 1 pod khác theo template, khi đó ==IP address sẽ thay đổi==

*Problem:* Khi được tạo lại, pod sẽ thay đổi ip của chính nó, nếu ip này được sử dụng trong các app liên quan thì sẽ phải thay đổi rất nhiều. 

### Services
Để giải quyết vấn đề Pod sau khi được tạo lại sẽ thay đổi IP address, thì k8s có giải pháp là service
- Service có IP address cứng không thay đổi, kể cả khi pod được recreate lại
- Dòng đời của pod không liên quan tới nhau.
- Mỗi 1 service sẽ có 1 URL riêng để truy cập tới nó 

Service thường được truy cập thông qua URL thông qua Ingress network. 

### Config Map & Secret
Trong các file config để tạo ra pod, thường có sử dụng các thông số như: URL service, URL DB, USERNAME, PASSWORD... K8s cung cấp _config map_, _secret_ để lưu trữ các thông số này.

- _secret_: Lưu trữ thông tin sensitive để cung cấp cho các dịch vụ khác
	- Chỉ lưu secret data
	- base64 encode
- _config map_: Lưu trữ thông tin 

### Deployment & StateFUL Set
- _Deployment_: Những app StateLess, chạy độc lập, sẽ sử dụng Deployment. Deployment là 1 kịch bản giúp định nghĩa số lượng ReplicaSet sẽ được tạo ra, các Pod tạo ra sử dụng template gì? và có cấu hình ra sao.
	![[Pasted image 20211113221504.png]]
- _StateFUL Set_: Những dạng app như Database, cần độ consistent cao, sẽ sử dụng StateFul Set 

## K8s Architecture
![[Pasted image 20211113215539.png]]

- _API Server_: client giao tiếp với hệ thống k8s thông qua _API Server_. API Server thực hiện các công việc như validate request 
- _Scheduler_: Có trách nhiệm tìm xem trong các node đã đăng ký Node nào còn tài nguyên nhiều để có thể triển khai node mới. ==Khi Pods bị lỗi ai sẽ chịu trách nhiệm?==
- _Controller Manager_: Chịu trách nhiệm quản lý các states của Pods. Khi có vấn đề xuất hiện, controller Manager thực hiện lại quy trình
	![[Pasted image 20211113220450.png]]
- _etcd_: được sử dụng như 1 database lưu lại các thông tin liên quan:
	- Is the cluster healthy?
	- What resources are available?
	- Did the cluster state change?

## Tools & Terms
### Minikube
Minikube là chương trình thường được sử dụng dưới máy local. minikube sẽ tạo ra: 
- Virtual box trên laptop
- Node chạy trên virtual box này
- 1 node k8s cluster
- dành cho môi trường DEV & Testing

### kubeclt 
Bộ lệnh dùng để điều khiển

### Namespace
Dùng để tổ chức các resources trong cluster 1 các rõ ràng và tổng thể. 1 cluster có thể có nhiều namespaces.
![[Pasted image 20211113222016.png]]
Những công dụng của namespace:
- phân chia resource cho 2 team projects 
- 2 projects có thể sử dụng chung trên app mà không bị conflict
- 2 phiên bản cùng chung trên 1 cluster và dùng chung 1 số resource được
	![[Pasted image 20211113222306.png]]
- Giới hạn quyền truy cập được từng Team:
	- Team A ----truy cập----> resource A
	- Team B ----truy cập----> resource B
- ==Lưu ý==: Khi sử dụng namespace trong kubectl thường phải cung cấp thông số --name-namespace

sử dụng lệnh
`kubens: liệt kê danh sách namespace`

## [[K8s Ingress | Ingress]]
Ingress Network là 1 service giúp client truy cập vào các service bên trong k8s
## Helm
Helm là package manager của k8s sẽ lưu trữ các Charts.
- _Chart_ là:
	- Bundle of YAML Files
	- Create your own Helm Chart with Helm
	- Push them to Helm Repository
	- Download and use existing ones
	
	
## [[K8s Volume | Volume]]

## [[K8s Persistent Storage| Persistent Volume]]

---
Tags: [[Kubernetes]]