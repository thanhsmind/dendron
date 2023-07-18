---
alias: 
- Docker API
type: programing 
---
# Traefik Docker API

## Setup
Cấu hình của Traefik có thể được define với Docker API  thông qua docker-compose. Sử dụng `command`, `labels`. 
==Lưu ý==: `commands` cần có option `--docker` để khai báo sử dụng Docker API cho Traefik.

```yaml
version: "3.3"

services:

  traefik:
    image: "traefik:v2.5"
    container_name: "traefik"
    command:
      #- "--log.level=DEBUG"
      - "--api.insecure=true"
      - "--providers.docker=true"
      - "--providers.docker.exposedbydefault=false"
      - "--entrypoints.web.address=:80"
    ports:
      - "80:80"
      - "8080:8080"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock:ro"

  whoami:
    image: "traefik/whoami"
    container_name: "simple-service"
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.whoami.rule=Host(`whoami.localhost`)"
      - "traefik.http.routers.whoami.entrypoints=web"
```


---
Tags: [[Traefik]]
References: 
- https://doc.traefik.io/traefik/user-guides/docker-compose/basic-example/
Related: 
- [[Traefik]]