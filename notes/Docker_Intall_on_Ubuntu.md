---
type: programing 
---
# Docker Engine

## Install Docker
```bash
sudo apt-get update
sudo apt-get upgrade -y

sudo apt-get -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
sudo groupadd docker
# Do this if to set up a non-privileged user to run Docker
# sudo usermod -aG docker ubuntu
sudo systemctl enable docker


```

--- 
Tags: [[DEV/Docker]] - [[DevOps]]
Related: 
- [[Docker Swarm]]