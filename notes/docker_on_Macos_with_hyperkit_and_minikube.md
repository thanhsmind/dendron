# docker on Macos with hyperkit and minikube
## Install docker on macos
```sh
# remove current docker
brew uninstall docker

# Install Hyperkit
brew install hyperkit
# Make sure hyperkit installed
hyperkit -v

# Install Docker CLI
brew install docker
# Note: Donot install `brew install --cask docker` this will install Docker Desktop

# Make sure docker installed
docker info

# Install Kubectl
brew install kubectl
# Install minikube
brew install minikube


# Start a Kubenetes cluster
minikube start --kubernetes-version=v1.19.14 --driver=hyperkit --container-runtime=docker

# View kubenetes context
minikube kubectl get nodes

# Install docker-compose
brew install docker-compose

# View Kubernetes cluster ip
minikube ip

# Add Ingress 
minikube addons enable ingress
# Add Ingress DNS
minikube addons enable ingress-dns

# Setup Load Balancer Services
# Assigning external IP to Load Balancer service. Without this, the service will have pending exter IP forever
minikube addons enable metallb


# install k9s manage
brew install k9s

```
### Fix Issues
*Logging in to Remote Registry*: Lấy Credential để pull images từ dockerhub
`brew install docker-credential-helper`
Update vào file  `~/.docker/config.json` với sửa key `credsStore` thành `credStore`

## Khởi tạo máy ảo kyperkit
```bash
minikube start

# config virtual máy có cấu hình
minikube config set cpus 2
minikube config set memory 4GB
minikube config set disk-size 10GB
minikube config set driver hyperkit

# xem lại config
minikube config view

```

## Biến Env cho docker
```bash
minikube docker-env 
# To point your shell to minikube's docker-daemon, run: 
eval $(minikube -p minikube docker-env)

```

## Mount folder to docker
```bash
minikube mount $PWD:$PWD
```

^6fb9b2

## Setup with .zshrc
Start Minikube
`minikube start --mount-string="/Users/$USER/ghq:/Users/$USER/ghq"`

Setup docker run
`eval $(minikube docker-env)`

View ip
`minikube ip`

---
Ref:
- https://www.notion.so/thanhsmind/Goodbye-Docker-Desktop-Hello-Minikube-by-Abhinav-Sonkar-Sep-2021-ITNEXT-5cf6a37fee1e46768680a007a8a14355
- https://minikube.sigs.k8s.io/docs/handbook/addons/ingress-dns/