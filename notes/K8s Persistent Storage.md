---
type: devops
---
# K8s Persistent Storage

Persistent Storage laf loaij Storage tồn tại độc lập với các POD, khi POD bị tắt hoặc bị xoá, thì dữ liệu lưu trữ trong Persistent Storage sẽ vẫn còn.

![[Screen Shot 2021-11-16 at 11.25.22 AM.png]]

## Persistent Volume(PV)
Persistent Volume(PV) giống như các volume được khái báo bình thường, chỉ khác 1 điểm là nó tồn tại độc lập khỏi pod.  PV giống như 1 node resource của cluster.  Có nhiều loại Persistent Volume(PV) như:
- glusterfs
- nfs
- csi
- ...
## Persistent Volume Claim(PVC)
Muốn sử dụng [[#Persistent Volume PV]] thì phải tạo Persistent Volume Claim(PVC). PVC là yêu cầu sử dụng PV. 
Persistent Volume Claim(PVC) có thể yêu cầu: 
- Tài nguyên CPU
- Bộ nhớ cần dùng
- Phân quyền truy cập
	- *ReadWriteOnce*: Volume được mount vào 1 node, và có thể Read, Write bởi node đó
	- *ReadOnlyMany*: Volume có thể được mount bởi nhiều nodes, và chỉ Read-only
	- *ReadWriteMany*: Volume có thể được mount bởi nhiều node và Read & Write
	- *ReadWriteOncePod*: Volume chỉ được mount vào 1 pod, và chỉ có pod đó mới được Read & Write được.

Giống Pod sử dụng tài nguyên của Node. PVC sử dụng tài nguyên của PV. Pod có thể request cụ thể các tài nguyên có thể sử dụng của Node(CPU& Memory), PVC thì request cụ thể dung lượng sử dụng, quyền truy cập vào PV.
## Commands
Xem thông tin chi tiết về Persistent Volume(PV) 
`kubectl get pv [pv-name]`
Xem thông tin chi tiết về Persistent Volume Claim(PVC)
`kubectl get pvc [pvc-name]`

## Example
Khỏi tạo PV, PVC, Pod sử dụng PVC.

### Khởi tạo Persistent Volume
Tạo file `example-pv-volume.yml`
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
	name: example-pv-volume
	labels:
		type: local
spec:
	storageClassName: hostpath
	capacity:
		storage: 10Gi
	accessModes:
		- ReadWriteOnce
	hostPath:
		path: "/data"
```
Apply file 
`kubectl apply -f example-pv-volume.yml`
Xem thông tin của PV mới được tạo 
`kubectl get pv example-pv-volume`

Persistent Volume(PV) được tạo dạng `hostPath`. hostPath Persistent Volume gắn file hoặc folder của node máy chủ vào pod để làm không gian lưu trữ.

### Tạo PersistentVolumeClaim(PVC)
Tạo file `example-pv-claim.yaml`
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
	name: example-pv-claim
spec:
	storageClassName: hostpath
	accessModes:
		- ReadWriteOnce
	resources:
		requests:
			storage: 4Gi
```
Tạo PersistentVolumeClaim 
`kubectl apply -f example-pv-claim.yml`

### Pod sử dụng PersistentVolumeClaim(PVC)
Tạo file `pod-use-pvc.yaml`
```yaml
apiVersion: v1
kind: Pod
metadata:
	name: example-pv-pod
spec:
	containers:
		- name: task-pv-container
		  image: nginx
		  ports:
		  	- containerPort: 80
			  name: "http-server"
		  volumeMounts:
		  	- mountPath: "/usr/share/nginx/html"
			  name: example-pv-storage
	volumes:
		- name: example-pv-storage
		  persistentVolumeClaim:
		  	claimName: example-pv-claim
```

---
Ref:
- https://viblo.asia/p/kubernetes-storage-hoc-cach-su-dung-persistent-volume-pv-va-persistent-volume-claim-pvc-Qpmleyynlrd
- https://kubernetes.io/docs/concepts/storage/persistent-volumes/