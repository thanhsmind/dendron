---
type: programing 
---
# Docker Swarm Cấu hình Certbot cho HTTPS
## Generate new Certificate.
Cấu hình service Certbot để quản lý việc generate certificate. ==Không nên chạy nhiều lần  nếu khống sẽ bị lock==. Thường 1 tháng chạy lại 1 cái mới tránh cho chứng chỉ hết hạn. Letsencrypt cho phép chứng chỉ 90 ngày.
```yaml
  version: "3.7"

  services:
    certbot:
      image: certbot/certbot
      container_name: certbot
      volumes:
        - certbot-etc:/etc/letsencrypt
        - wordpress:/var/www/html
        - ../../themes/dt-the7:/var/www/html/wp-content/themes/dt-the7/
        - ../../plugins:/var/www/html/wp-content/plugins/
        - ./:/var/log/letsencrypt/
    
      command: certonly --webroot --webroot-path=/var/www/html --email thanh@thetalent.pro --agree-tos --no-eff-email --force-renewal -d thetalent.pro -d www.thetalent.pro

  volumes:
    certbot-etc:
      external:
        name: web-thetalentpro_wordpress
    wordpress:
      external:
        name: web-thetalentpro_wordpress

```

## Renew certificate
```bash
#!/bin/bash

  

COMPOSE="/usr/bin/docker-compose --no-ansi"

DOCKER="/usr/bin/docker"

  

cd /home/www/web-thetalentpro/app/ssl

$COMPOSE run certbot renew --dry-run && $DOCKER service update web-thetalentpro_webserver
```
`--dry-run` : dành cho việc test generate certificate

![[certbot-generate-certificate.png]]

### Cấu hình auto renew
```bash
sudo crontab -e
```
Cấu hình crontab với dòng lẹnh 
```bash
...
22 03 * * 2,7 /home/sammy/wordpress/ssl_renew.sh >> /var/log/cron.log 2>&1
```

Bỏ test bằng cách bỏ option `--dry-run`
```bash
#!/bin/bash

  

COMPOSE="/usr/bin/docker-compose --no-ansi"

DOCKER="/usr/bin/docker"

  

cd /home/www/web-thetalentpro/app/ssl

$COMPOSE run certbot renew  && $DOCKER service update web-thetalentpro_webserver
```