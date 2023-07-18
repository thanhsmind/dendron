---
type: programing 
---
# Docker Backup & Restore

nguyenphuongthanhf/jenkins
## Push container to Local images
```
docker commit -p CONTAINER-ID IMAGE-NAME
```

## Backup Images
```
docker save -o IMAGE-NAME.tar IMAGE-NAME
```
## Restore Images
```
docker load -i IMAGE-NAME.tar
```
## Push image to repository 
```
docker tag IMAGE-NAME localhost:5000/IMAGE-NAME:v2
docker push localhost:5000/IMAGE-NAME:v2
```

## Backup container 
```
docker run --rm --volumes-from jenkins_jenkins_1 -v $(pwd):/backup jenkins31 tar cvf /backup/backup.tar /var/jenkins_home
```
## Restore container from backup
```
docker run --rm --volumes-from jenkins_jenkins_1 -v $(pwd):/backup jenkins2-277-1 bash -c "cd /var/ && tar xvf /backup/jenkins_bk_24mar2021.tar --strip 1"
```
docker tag jenkins2-277-1 nguyenphuongthanhf/jenkins:v2.277.1

docker commit -p ecc607cd0c48 jenkins2-277-1

docker save -o jenkins2-277-1.tar jenkins2-277-1

rm /var/jenkins_home/jobs/*/builds/* -rf

---
Tags: [[DevOps]] [[DEV/Docker]]