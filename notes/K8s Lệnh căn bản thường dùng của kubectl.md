---
type: devops
---
# K8s Lệnh căn bản thường dùng của kubectl

##  CRUD command

*Create deployment*
`kubectl create deployment [name]`
*Edit deployment*
`kubectl edit deployment [name]`
*Delete deployment*
`kubectl delete deployment [name]`

### Use configuration file for CRUD
*Apply a configuration file*
`kubectl apply -f [file name]`
*Delete with configuration file*
`kubectl delete -f [file name]`

## Status of different K8s components
`kubectl get nodes | pod | services | replicaset | deployment `

## Debug pods
*Log to console*
`kubectl logs [pod name]`
*Get interactive terminal* 
`kubectl exec -it [pod name] -- bin/bash`
*Get info about pod*
`kubectl describe pod [pod name]`