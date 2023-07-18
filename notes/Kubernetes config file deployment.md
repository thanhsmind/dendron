---
type: devops
---
# Kubernetes config file

Deployment Config file
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
	name: nginx-development
	labels: Nginx
spec:
	replicas: 2
	selector:
	template:

```

Service config file
```yaml
apiVersion: v1
kind: Service
metadata: 
	name: nginx-service
spec:
	selector:
	ports:
```

Configuration file gồm 3 phần
## 1. metadata
```yaml
metadata:
	name: nginx-development
	labels: Nginx

```
## 2. specification
### Deployment Config File
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: nginx
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - image: nginx:1.16
        name: nginx
        ports:
        - containerPort: 8080
```
*template* dùng để tạo blueprint khi khởi tạo các pods trong giai đoạn deployment. 

### Service config file
```yaml
apiVersion: v1
kind: Service
metadata: 
	name: nginx-service
spec:
	selector:
		app: nginx
	ports:
		- protocol: TCP
		  port: 80
		  targetPort: 8080
```
Kết nối service vào deployment.
![[Screen Shot 2021-11-04 at 9.49.58 PM.png]]


### Ports in Service and Pod
![[Screen Shot 2021-11-04 at 9.53.06 PM.png]]

## 3. status
*status* tự động được thêm vào bởi k8s khi hoạt động. K8s sẽ cập nhật thường xuyên tình trạng. Thông số status sẽ được lưu trong etcd và được lấy ra khi cần.

```yaml
status:
  availableReplicas: 1
  conditions:
  - lastTransitionTime: "2021-11-04T11:03:31Z"
    lastUpdateTime: "2021-11-04T11:03:31Z"
    message: Deployment has minimum availability.
    reason: MinimumReplicasAvailable
    status: "True"
    type: Available
  - lastTransitionTime: "2021-11-04T11:03:14Z"
    lastUpdateTime: "2021-11-04T11:03:31Z"
    message: ReplicaSet "nginx-depl-5c8bf76b5b" has successfully progressed.
    reason: NewReplicaSetAvailable
    status: "True"
    type: Progressing
```