---
type: programing 
---
# Install WSL2 on Window 10

## Cài đặt WSL

### Run PowerShell as admin

```
wsl --install
```
****
### Change container location.

[https://grishagin.com/ubuntu/2020/10/26/change-wsl2-container-location.html](https://grishagin.com/ubuntu/2020/10/26/change-wsl2-container-location.html)

### Install GUI app

[https://opticos.github.io/gwsl/](https://opticos.github.io/gwsl/)

### Add to .bashrc to run GUI app *important*

```
export DISPLAY_NUMBER="0.0" 
export DISPLAY=$(grep -m 1 nameserver /etc/resolv.conf | awk '{print $2}'):$DISPLAY_NUMBER
```

### Install Systemd

[https://github.com/DamionGans/ubuntu-wsl2-systemd-script](https://l.workplace.com/l.php?u=https%3A%2F%2Fgithub.com%2FDamionGans%2Fubuntu-wsl2-systemd-script&h=AT0RKhodglgM89GGYwW2xf75s7tiE1N72T6WaHMYiynz3BJ9wQnLrlf-oDlT2yp6pJxxjU5GE3rhO8G33dcLmH3dm14Fq6ULH8xbN7VZcGJDqssDE2LdHn7xHuiW5Wbh7pTjq9IipQBdS0e8O5Ex0Kg)

```
git clone https://github.com/DamionGans/ubuntu-wsl2-systemd-script.git
cd ubuntu-wsl2-systemd-script/
bash ubuntu-wsl2-systemd-script.sh
# Enter your password and wait until the script has finished
```

### Cấu hình Instance
Cập nhật tại file `NotePad $USERPROFLE$/.wsconfig `

#### setup ram for instance wsl2 
```
[wsl2]
memory=4GB # Limits VM memory in WSL 2 up to 4GB
```

Cấu hình chi tiết tại 
```
#https://docs.microsoft.com/en-us/windows/wsl/wsl-config#change-the-default-user-for-a-distribution
[wsl2]
memory=4GB # Limits VM memory in WSL 2 up to 4GB

# Set the user when launching a distribution with WSL
[user]
default = thanhnp

# Set a command to run when a new WSL instance launches. 
[boot]
command = service docker start

# Network host settings that enable the DNS server used by WSL 2. This example changes the hostname, sets generateHosts to false, preventing WSL from the default behavior of auto-generating /etc/hosts, and sets generateResolvConf to false, preventing WSL from auto-generating /etc/resolv.conf, so that you can create your own (ie. nameserver 1.1.1.1).
# [network]
# hostname = DemoHost
# generateHosts = false
# generateResolvConf = false

# Automatically mount Windows drive when the distribution is launched
#[automount]

# Set to true will automount fixed drives (C:/ or D:/) with DrvFs under the root directory set above. Set to false means drives won't be mounted automatically, but need to be mounted manually or with fstab.
#enabled = true

# Sets the directory where fixed drives will be automatically mounted. This example changes the mount location, so your C-drive would be /c, rather than the default /mnt/c. 
#root = /

# DrvFs-specific options can be specified.  
#options = "metadata,uid=1003,gid=1003,umask=077,fmask=11,case=off"

# Sets the `/etc/fstab` file to be processed when a WSL distribution is launched.
#mountFsTab = true
```


### Install Window terminal

[https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701#activetab=pivot:overviewtab)

## Setup Ubuntu

### Install common packages

```
sudo apt update && sudo apt -y upgrade && sudo apt -y autoremove
sudo apt install build-essential git curl terminator vim dnsmasq -y
```

### Install docker

```
curl -sSL https://get.docker.com/ | sudo sh
```

### Install Google Chrome

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb 
sudo apt -y install ./google-chrome-stable_current_amd64.deb
```

### Install PHPStorm

[https://www.jetbrains.com/help/phpstorm/installation-guide.html#standalone](https://www.jetbrains.com/help/phpstorm/installation-guide.html#standalone)

```
sudo snap install phpstorm --classic
```

### Ubuntu settings
#### Default user Login ubuntu cli 
```
# Ubuntu version
Ubuntu config --default-user [username]
# Ubutnu 20.04
ubuntu2004 config --default-user [username]
# Ubuntu 18.04
ubuntu1804 config --default-user [username]
```











