---
alias:
- Cấu hình Stack DB
type: programing 
---
# Docker Swarm Cấu hình Stack DB

```yaml

  version: "3.7"

  services:
    db:
      image: mysql:5.7
     # container_name: db
     # restart: unless-stopped
      command: [ "mysqld",
              "--character-set-server=utf8mb4",
              "--collation-server=utf8mb4_unicode_ci",
              "--bind-address=0.0.0.0",
              "--innodb_large_prefix=true",
              "--innodb_file_format=barracuda",
              "--innodb_file_per_table=true" ]
      environment:
        MYSQL_DATABASE: webthetalentpro
        MYSQL_USER: thetalentproweb
        MYSQL_PASSWORD: thetalentprocamcui
        MYSQL_RANDOM_ROOT_PASSWORD: "Pr!m#rW0rd"
      volumes:
        - db:/var/lib/mysql
      networks:
        - dbnet

  volumes:
    db:
   

  networks:
    dbnet:
        external: true

```

Specifying "container_name" is unsupported because it would break the ability to scale or perform updates (a container name must be unique within the docker engine). Let swarm name the containers and reference your app on the docker network by it's service name.

Specifying "depends_on" is not supported because containers may be started on different nodes, and rolling updates/failure recovery may remove some containers providing a service after the app started. Docker can retry the failing app until the other service starts up, or preferably you configure an entrypoint that waits for the dependencies to become available with some kind of ping for a minute or two.
```
     # container_name: db
     # restart: unless-stopped
	 # depends_on
```

### Thêm DB networks  vào swarm 
```shell
docker network create dbnet --scope swarm --driver overlay
```

### Launch Stack with name `db`
```shell
  docker stack deploy --compose-file docker-compose.yml db
```

### Check database config. 
```shell
docker exec -it db_db.1.q857g8vxzdzbvtw1byd42wcwm mysql -u root -p
```

### Import database hiện tại vào
```shell
 docker exec -i db_db.1.q857g8vxzdzbvtw1byd42wcwm sh -c 'exec mysql -uthetalentproweb -p"thetalentprocamcui" webthetalentpro' < ./wordpress_bk.sql
 
```

### Backup database
```bash
docker exec db sh -c 'exec mysqldump -uthetalentproweb -p"thetalentprocamcui" --no-tablespaces  -y webthetalentpro' > /home/www/wordpress_bk.sql 
```
--- 
Tags: [[DEV/Docker]] - [[DevOps]] - [[Docker Swarm]] - [[Wordpress]]
References:
- [[Docker Commands]]
Related: 
- [[Docker Swarm How to setup Wordpress production]]