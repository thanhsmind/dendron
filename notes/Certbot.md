---
type: programing 
---
# Certbot

## Lưu ý:
- Nếu request mới quá nhiều lần sẽ bị khoá không cho renew mới trong 7 ngày
	"already issued for this exact set of domains in the last 168 hours"
- `/etc/letsencrypt/archive`
	Các file trong đây sẽ được link tới thư mục live.==Không được xoá mất các file trong này==
## Utilities
**Xoá tất cả file CSR cũ để giải phóng bộ nhớ**
Theo [@schoen former Certbot](https://community.letsencrypt.org/t/have-any-certbot-users-used-etc-letsencrypt-keys-csr-archive/78425) File chứa trong 
- `/etc/letencrypt/csr`
- `/etc/letencrypt/keys`
==Sẽ không được sử dụng lại bởi Certbot. Chúng chỉ mang tính chất tham chiếu, nên có thể xoá thoải mái.==
Nếu muốn xoá trong 91 ngày.
```bash
#**List** all CSR files not modified during the past 91 days:  
find /etc/letsencrypt/csr/ -type f -name ‘*.pem’ -mtime +91 -exec ls -lah {} ;

#**Delete** all CSR files not modified during the past 91 days:  
find /etc/letsencrypt/csr/ -type f -name ‘*.pem’ -mtime +91 -exec rm -f {} ;

```


---
Tags: [[DevOps]]
Related: 
- https://techsparx.com/software-development/docker/damp/nginx-cron-ssl.html
- https://techsparx.com/software-development/docker/damp/cronginx-usage.html
- https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose
- https://certbot.eff.org/docs/using.html?highlight=renewal#setting-up-automated-renewal
- 
- [[Docker Swarm Cấu hình Stack Application]]
References:
