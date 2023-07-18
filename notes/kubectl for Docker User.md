---
type: devops
---
# kubectl for Docker User


| docker command         | kubernetes command                 |
| ---------------------- | ---------------------------------- |
| docker run             | kubectl create deployment          |
| docker ps -a           | kubectl get po                     |
| docker attach          | kubectl attach -it pod-name        |
| docker exec            | kubectl exec pod-name              |
| docker logs            | kubectl logs -f pod-name           |
| docker stop/ docker rm | kubectl delete deployment pod-name |
| docker version         | kubectl version                    |
| docker info            | kubectl cluster-info                                   |

---
Tags: [[Kubernetes]]