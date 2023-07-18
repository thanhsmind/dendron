# K8s first app

Trong K8s thì pod là thành phần nhỏ nhất có thể giao tiếp. Pod giống như 1 wrapper ngoài của container, giúp thêm nhiều tiện ích giao tiếp với container như: health check, ...

Nhưng khi sử dụng thì không tạo pod trực tiếp mà thông qua bản thiết kế *Deployment*. 
`kubectl create deployment [name] --image=IMAGE-NAME`

Khi *Deployment* được tạo K8s sẽ tạo ra các thành phần liên qua như
- pod: `kubectl get pod`
- replicaset: `kubectl get replicaset` Thông tin về số lượng replica đã được tạo. ReplicaSet quản lý các replica của pod

![[Pasted image 20211104181820.png]]


---
Tags: [[Kubernetes]]