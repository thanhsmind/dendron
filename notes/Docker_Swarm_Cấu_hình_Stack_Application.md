---
alias:
- Cấu hình Stack Application
type: programing 
---
# Docker Swarm Cấu hình Stack Application

Cấu hình Stack Application trong docker-compose.yml
```yaml
  version: "3.7"

# stack dont support depends_on, container_name, restart
  services:
    wordpress:
      image: wordpress:5.8.1-php7.4-fpm-alpine
    #  depends_on:
    #    - db
    #  container_name: wordpress
    #  restart: unless-stopped
      environment:
        WORDPRESS_DB_HOST: db
        WORDPRESS_DB_USER: thetalentproweb
        WORDPRESS_DB_PASSWORD: thetalentprocamcui
        WORDPRESS_DB_NAME: webthetalentpro
      volumes:
        - wordpress:/var/www/html
        - ../themes/dt-the7:/var/www/html/wp-content/themes/dt-the7/
        - ../plugins:/var/www/html/wp-content/plugins/
      networks:
        - app-network
    
    webserver:
      image: nginx:1.21.3-alpine
    # depends_on:
    #   - wordpress
    # container_name: webserver
    # restart: unless-stopped
      ports: 
        - "80:80"
        - "443:443"
      volumes:
        - wordpress:/var/www/html
        - ../nginx-conf:/etc/nginx/conf.d
        - certbot-etc:/etc/letsencrypt
        - ../themes/dt-the7:/var/www/html/wp-content/themes/dt-the7/
        - ../plugins:/var/www/html/wp-content/plugins/  
      networks:
        - app-network

  
  
  volumes:
    wordpress:
    certbot-etc:

  networks:
    app-network:
      driver: bridge   


```

### Thêm App networks  vào swarm 
```shell
docker network create app-network --scope swarm --driver overlay
```

### Launch Stack with name `web-thetalentpro`
```shell
 docker stack deploy --compose-file docker-compose.yml web-thetalentpro
```

### Check service running
```bash
docker service ls
```
![[docker-swarm-service-ls.png]]

