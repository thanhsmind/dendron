---
type: devops
---
# k8s config minikube run docker

## Commands
```sh
docker_start () {
 minikube start --disk-size 10GB  --mount-string='/Users/$USER/Development/projects:/Users/$USER/Development/projects' ;
 eval $(minikube -p minikube docker-env);
docker info;
}

```

## How to run docker with minikuber
** Mount thư mục code vào trong Docker **
![[docker on Macos with hyperkit and minikube#^6fb9b2]]
**Start Kubernetes cluster**
Khởi tạo 1 cluster để chạy docker
```
minikube start --kubernetes-version=v1.22.3 --driver=hyperkit --container-runtime=docker
```
- `--kubernetes-vesion=v1.22.3`: là version kubernetes sẽ chạy

**Kiểm tra xem version cluster** mới khởi tạo xem có đúng không
`minikube kubectl get node`

**Thiết lập kết nối với docker**
` eval $(minikube docker-env)`


---
- References:
	- [Run docker with minikube](https://itnext.io/goodbye-docker-desktop-hello-minikube-3649f2a1c469)