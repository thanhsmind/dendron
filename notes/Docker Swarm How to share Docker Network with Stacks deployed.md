---
type: programing 
---
# Docker Swarm How to share Docker Network with Stacks deployed
Problem: Hiện đã có sẵn 1 Stack[^1] muốn kết nối với các Docker node trong Swarm. 

Ví dụ ứng dụng có:
- Application Layer: NGINX chạy HTTPS, Wordpress Sites
- Database layer: MYSQL, có thể cài thêm PHPMyAdmin

Với kiến trúc trên ta tách thành 2 Stacks, định nghĩa trong 2 Compose files:
- Application Layer composer sử dụng 2 networks:
	- `servernet`: Application layer containers to communicate with each other
	- `dbnet`: to communicate with the database
- Database layer composer file sử dụng network:
	- `dbnet`: mạng dùng chung cho MySQL và PHPMyAdmin

Tạo 2 mạng với scope swarm:
```bash

$ docker network create dbnet --scope swarm --driver overlay 

$ docker network create servernet --scope swarm --driver overlay
```

Cấu hình Networks
Database Compose File:
```bash
networks: 
	dbnet: 
		external: true
```

Application Layer Composer File:
```bash
networks:
    servernet:
        external:
            name: servernet
    dbnet:
        external:
            name: dbnet
```
Cho Swarm Stacks, các networks pahri được khai báo ở các Compose file khác nhau. và đòi hỏi `external: true`

--- 
Tags: [[DevOps]]
References:
- [How to share a Docker network between Stacks deployed to a Docker Swarm](https://techsparx.com/software-development/docker/swarm/share-networks.html)
	
Related: 
- [[Docker Swarm]]

[^1]: Cụm Server được định nghĩa trong docker-compose.yml