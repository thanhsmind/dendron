---
title: 'Upgrade To Php 8.1 Amazon Linux 2'
date: '2020-01-02'
type: programing 
tags: ["php", 'aws', "amazon linux 2"]
---

# Upgrade To Php 8.1 Amazon Linux 2


## Install httpd
### Install
`sudo yum install httpd -y`
### Start
`sudo systemctl start httpd`
### Restart
`sudo systemctl restart httpd`
### Status
`sudo systemctl status httpd`
### Check version
`httpd -V`

## Install Php 8
`sudo amazon-linux-extras install php8.1`

### Check version
`php -v`

```
yum install php81
yum install php81-php-{cli,fpm,mysqlnd,devel,gd,mbstring,curl,xml,pear,bcmath,json,opcache,ldap}

php81 --modules

 rm /bin/php -rf
 ln -s /opt/remi/php82/root/usr/bin/php /bin/php
systemctl reboot

```

## Install php extensions
Now install PHP packages from the repository.
```
sudo yum clean metadata
sudo yum install php php-{pear,cgi,common,curl,mbstring,gd,mysqlnd,gettext,bcmath,xml,fpm,intl,zip}
```
[How to install PHP 8.0 on Amazon Linux 2 AWS – MistOnline](https://mistonline.in/wp/how-to-install-php-8-0-on-amazon-linux-2-apache-2-4/)