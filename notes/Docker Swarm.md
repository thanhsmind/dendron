---
type: programing 
---
# Docker Swarm
https://xuanthulab.net/tim-hieu-ve-docker-swarm-khoi-tao-va-su-dung.html
## [[Tại sao cần Docker Swarm]]
Với các project nhỏ, có thể sử dụng đơn thuần Docker Engine deploy trên 1 máy(vps). Nhưng khi dự án lớn, cần phải scale up lên thành nhiều máy(vps) thì việc deploy trở nên rất khó khăn. **Docker Swarm** ra đời với mục đích giúp đơn giản hoá quá trình này.

## [[What is Docker Swarm]]
Using Swarm raises the possibility of having multiple servers. Swarm is a Container Orchestration system that is native to Docker. It automatically handles communication between services in a Docker Swarm Cluster, and handles distributing services across a Cluster.
### Tính năng của Docker Swarm
- **Cluster management integrated with Docker Engine**: Quản lý cluster với Docker Engine bằng Docker CLI để tạo Swarm.
- **Decentralized design**: Docker Swarm được thiết kế dạng phân cấp với 2 loại node: Managers và worker bằng Docker Engine.
- **Declarative sẻvice model**: Docker Engine sử dụng phương thức khai báo cho phép định nghĩa trạng thái mong muốn của các dịch vụ khác nhau trong stack. Ví dụ: web frontend, database backend, message queueing.
- **Scaling**: Mỗi service có thể khai báo số lượng task muốn run. Khi scale up, down, thì Docker Swarm manager sẽ tự động thêm vào hoặc xoá bớt các task này.
- **Desired state reconciliation**: Ví dụ khi có 1 service với 10 replicas của 1 container, khi có 1 VPS có chứa 2 trong 10 replicas này bị crash, lúc này Swarm manager sẽ tiến hành tạo thêm 2 replicas mới thay thế cho 2 replicas đã bị cash đó, và tiến hành chuyển 2 replicas mới này vào các worker đang run. 
- **Multi-host networking**: Có thể chỉ định overlay network cho các service. Swarm manager sẽ tự động gán địc chỉ IP cho các container trên overlay network khi nó cập nhật application.
- **Service discovery**: Swarm mânger node gán mỗi sẻvice trong swarm 1 DNS duy nhất , và có thể truy vấn được thông qua DNS này.
- **Load balancing**: có thể expose các pỏt cho các service  tới load balance để giao tiếp với bên ngoài.
- **Secure by default**: Các service giao tiếp với nhau thông qua giao thức bảo mật TLS. Có thể tuỳ chỉnh sủe dụng chứng chỉ ký tự rôt hoặc chứng chỉ từ một custom root CA.
- **Rolling updates**: Swarm giúp update image của 1 service hoàn toàn tự động. Swarm manager giúp kiểm soát độ trễ giữa service deploy tới các node khác nhauvaf có thể rolling back bất cứ lúc nào.

## [[Kiến trúc Docker Swarm]]
![[kien-truc-swarm.png]]

![[swarm-config.png]]

- **Swarm**: là 1 cluster của 1 hoặc nhiều Docker Engine đang chạy trong chế độ Swarm. Các Docker Engine sẽ được cấu hình thành các service với số lượng replicas.
- **Node**: Node là 1 máy vật lý hoặc máy ảo đang chạy phiêm bản Docker Engine trong chế độ Swarm. Node gồm 2 loại: 
	- **Manager Node**: Là node nhận các define service( docker-compose.yml). Node này quản lý và điều phối các task đến các node Worker. Bản thân Manager Node cũng là Worker Node.
	- **Worker Node**: Node nhận thực thi các task từ Manager Node.
- **Service**: 1 service xác định image của container và số lượng các replicas mong muốn khi chạy trong swarm.
- **Task**: Tác vụ Worker node phải thực hiện. Task sẽ được node manager phân bổ xuống. 1 Task là 1 Docker Container và chứa các lệnh chạy container bên trong

Thông thường các Docker được quản lý bằng Docker CLI riêng biệt
![[b5dd65d9-82ca-43fc-be27-2588ab933abe.png]]

Với Docker Swarm thì sẽ quản lý chung thông qua 1 Docker CLI. Mọi tác vụ Scale up, down. Thêm node sẽ chỉ được thực hiện trên `Manager Node`
![[90beb86d-58c7-4ce2-ba57-42d85253f4d9.png]]

Docker Swarm giúp rollback lại version cũ nhanh chóng khi có 1 node bị lỗi.
![[cfb97cca-2506-407c-a46f-34cb40c01744.png]]

## Docker Swarm Init
Giả sử Hệ thống có 3 máy VPS: vps1, vps2, vps3

### Khởi tạo Swarm
Khi 1 máy ra lệnh chuyển nó chạy ở chế độ Swarm(swarm mode), lập tức nó trở thành 1 node trong swarm. Máy này được khởi tạo đầu tiên nên nó năm quyền kiểm soát toàn bộ, và nó gọi là `manager`. Chỉ `marnager` mới có quyền khởi tạo các dịch vụ chạy trên Swarm, xoá 1 node ra khỏi Swarm.

```bash
# On Digital Ocean this will give an error
docker swarm init --advertise-addr <IP Machine>
```

** Trên Server** Lỗi sẽ hiện ra
```bash
Error response from daemon: could not choose an IP address to advertise since this system has multiple addresses on interface eth0 (167.71.202.125 and 10.15.0.5) - specify one with --advertise-addr
```
Thường thì cloud sẽ có 2 ip cho mỗi máy:
- Public IP: có thể thay đổi khi restart máy, tuỳ dịch vụ 
- Private IP: Thường cố định dù có restart hay stop & restart.

```bash
root@test-wp-deployment:~# docker swarm init --advertise-addr 10.48.0.5
Swarm initialized: current node (yo5pzh0b6zujxz09qlnge5fjm) is now a manager.

```

### Xem Swarm hiện dang có node nào
```bash
docker node ls
```
![[docker-swarm-node-ls.png]]
Hình trên cho thấy Swarm hiện có 3 node, ở 3 máy khác nhau. trên mỗi node có các stack chạy 

### Thêm 1 node worker vào trong Swarm
Khi có nhiều máy chạy Docker Engine muốn gia nhập vào Swarm, thì sẽ dùng câu lệnh xin gia nhập, nó sẽ trở thành `worker node`.
Những `worker node` chỉ có khả năng chạy các services chứ không có quyền quản lý các node. 

```bash
#To add a worker to this swarm, run the following command:

docker swarm join --token SWMTKN-1-1ld23xh8orjh95zfbpnrh0j40g7ivhb2ttvcktbux47g1p94x0-0m7hhskivpshkjerqd0agff6t 10.48.0.5:2377

```
```bash
docker node ls
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
sfysjr8wstldv2wrmgqcrpozt *   vps1                Ready               Active              Leader              18.09.5
z4i90rojpknedxn52aa764k38     vps2                Ready               Active                                  18.09.5
7vdibj6lfdma874qc05tiuhr3     vps3                Ready               Active                                  18.09.5
```

### Thêm 1 node manager vào trong Swarm
```bash

#To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
docker swarm join-token manager
```

### Swarm có nhiều Node Manager
Bình thường Swarm có 1 node với vai trò là `manager node`. Trong tình huống có thể node manager có thể bị lỗi dẫn tới việc Swarm. Swarm có chứ năng đề xuất khi `manager node` có thể chuyển qua node khác khi `manager node`chính gặp vấn đề.
```bash
docker node promote NODEID
```

## HOW TO
- [[Docker Swarm How to share Docker Network with Stacks deployed]]
- [[Docker Swarm How to setup Wordpress production]]
- https://warlord0blog.wordpress.com/2021/03/17/traefik-swarm/
- https://dev.to/ohffs/traefik-v2-with-docker-swarm-2cgh

--- 
Tags: [[DEV/Docker]] - [[DevOps]]
References:
- https://viblo.asia/p/tim-hieu-docker-swarm-voi-vi-du-co-ban-4P856JmR5Y3
- Related: 
- [[Kubernetes]]