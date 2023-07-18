---
type: devops
alias: Ingress
---

# K8s Ingress

Ingress Network cho phép client có thể truy cập vào các service trong hệ thống k8s thông qua Domain.
![[Pasted image 20211114172647.png]]

Ingress sẽ route HTTP&HTTPS từ bên ngoài vào các services bên trong cluster
Traffic routing dựa vào các rules được định nghĩa trong Ingress Resource

## Ingress Controller
Ingress Controller có trách nhiệm phân phối traffic tới Ingress bên trong, thường với load balancer thông qua các rules được định nghĩa.
Ingress resource muốn hoạt động phải có 1 Ingress controller điều khiển. Khác với các loại controller khác của k8s, Ingress controller không tự động start với cluster. 
Có nhiều loại controller được cung cấp bởi bên thứ 3: 
- [Kong Ingress Controller for Kubernetes](https://github.com/Kong/kubernetes-ingress-controller#readme)
- [NGINX Ingress Controller for Kubernetes](https://www.nginx.com/products/nginx-ingress-controller/)
- [HAProxy Ingress Controller for Kubernetes](https://github.com/haproxytech/kubernetes-ingress#readme)
- [Traefik Kubernetes Ingress provider](https://doc.traefik.io/traefik/providers/kubernetes-ingress/)


## Ingress Resource
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
	name: minimal-ingress
	annotations:
		nginx.ingress.kubernetes.io/rewrite-target: /
spec:
	rules:
	- http:
		paths:
		- path: /testpath
		  pathType: Prefix
		  backend:
		  	service:
				name: test
				port:
					number: 80
```
- 3 Thông số bắt buộc của file Ingress Spec:
	- `apiVersion`
	- `kind`
	- `metadata`
		- `name`: Name của Ingress phải tuân theo DNS subdomain name.
		- `annotations`: Thường được sử dụng để config các option tuỳ theo [[#Ingress Controller]]. Ingress Controller khác nhau hỗ trợ các annotations khác nhau. 
## Ingress Rules
```yaml
spec:
	rules:
	- http:
		paths:
		- path: /testpath
		  pathType: Prefix
		  backend:
		  	service:
				name: test
				port:
					number: 80
					
```
HTTP rule bao gồm các thông tin: 

### Host (Optional)
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-wildcard-host
spec:
  rules:
  - host: "foo.bar.com"
    http:
      paths:
      - pathType: Prefix
        path: "/bar"
        backend:
          service:
            name: service1
            port:
              number: 80
  - host: "*.foo.com"
    http:
      paths:
      - pathType: Prefix
        path: "/foo"
        backend:
          service:
            name: service2
            port:
              number: 80
```
### paths
path sẽ dùng đề route tới service 

#### Path types
Mỗi 1 path trong Ingress đòi hỏi 1 path type tương ứng. `pathType` là bắt buộc trong config. Có 3 loại path types:
- `ImplementtationSpecific`: Việc Match URL loại này tuỳ thuộc vao IngressClass
- `Exact`: Match URL chính xác kể cả in hoa in thường
- `Prefix`: Match URL prefix split bởi `/`. 

##### Ingress class
```yaml
apiVersion: networking.k8s.io/v1
kind: IngressClass
metadata:
  name: external-lb
spec:
  controller: example.com/ingress-controller
  parameters:
    apiGroup: k8s.example.com
    kind: IngressParameters
    name: external-lb
```

### Backend
#### Default Backend
1 Ingress nếu không có rules nào khớp thì nó send toàn bộ traffic tới default backend. 
#### Resource backends
Resource Backend là 1 ObjectRef tới 1 Kubernetes Resource trong cùng namespace. 

---
Ref:
- [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress)

Related:
 - [[K8s HAProxy Ingress Controller | HAProxy Ingress Controller]]