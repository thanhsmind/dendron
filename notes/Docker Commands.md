---
type: programing 
---
# Docker Commands

## Basic commands
<dl>
	<dt><b>`docker ps`</b></dt>
    <dd>Cung cấp thong tin chi tiết về các container runtime. </dd>
	<dt><b>`docker ps -a`</b></dt>
    <dd>Thông tin chi tiết của container đang chạy hoặc đang bị tắt </dd>
	<dt><b>`docker rm CONTAINER-ID|CONTAINER-NAME`</b></dt>
    <dd>Xoá container </dd>
	<dt><b>`docker inspect CONTAINER-ID|CONTAINER-NAME`</b></dt>
    <dd>Xem thông tin chi tiết container </dd>
	<dt><b>`docker images`</b></dt>
    <dd>Danh sách các images đang có trong máy</dd>
	<dt><b>`docker volume ls`</b></dt>
    <dd>Xem danh sách các Volume đang có </dd>
	<dt><b>`docker volume inspect VOLUME-NAME`</b></dt>
    <dd>Xem chi tiết thông tin của volume</dd>
</dl>
## `docker swarm` commands
<dl>
	<dt><b>`docker swarm init --advertise-addr IP-ADDRESS`</b></dt>
   <dd>Init 1 swarm.</dd>
	<dt><b>`docker swarm join --token TOKEN-STRING 10.48.0.5:2377`</b></dt>
   <dd>Thêm 1 worker vào trong swarm. </dd>
	<dt><b>`docker swarm join-token manager`</b></dt>
   <dd>Thêm 1 manager vào trong swarm </dd>
	<dt><b>`docker network create dbnet --scope swarm --driver overlay`</b></dt>
   <dd>Join 1 network của stack vào chung network với swarm</dd>
</dl>

## `docker service` commands
Cách lệnh quản lý, cập nhật, scale dịch vụ đang thi hành trên node manager
<dl>
	<dt><b>`docker service ls`</b></dt>
  	<dd>Xem tất cả các services đã launch ( replicated)</dd>
	<dt><b>`docker service ps testservice`</b></dt>
  	<dd>Liệt kê các container cho dịch vụ có tên testservice</dd>
	<dt><b>`docker service logs testservice`</b></dt>
  	<dd>Kiểm tra log cho dịch vụ testservice</dd>
	<dt><b>`docker service scale testservice=n`</b></dt>
  	<dd>Scale - thay đổi số container cho dịch vụ testservice đang chạy thành n (1, 2, 3 ...) container</dd>
	<dt><b>`docker service update --image=ichte/swarmtest:php testservice`</b></dt>
  	<dd>Thay đổi Image</dd>
	<dt><b>`docker service update --limit-cpu="0.5" --limit-memory=150MB testservice`</b></dt>
  	<dd>Thay đổi tài nguyên CPU, MEM</dd>
	<dt><b>`docker service rm servicename`</b></dt>
  	<dd>Xóa dịch vụ testservice</dd>
</dl>

## `docker stack` commands
Quản lý các dịch vụ chạy trên swarm. Các dịch vụ này thường được mô tả trong file `docker-compose.yml`
<dl>
	<dt><b>`docker stack deploy --compose-file docker-compose.yml STACK-NAME`</b></dt>
  	<dd>Launch 1 stack với docker-compose.yml</dd>
	<dt><b>`docker stack ps --no-trunc STACK-NAME`</b></dt>
  	<dd>Xem log của Stack khi deploy để tim bug</dd>
	<dt><b> `docker stack ls`</b></dt>
	<dd>List danh sách stack đang có</dd>
	<dt><b>`docker stack ps`</b></dt>
	<dd>List các task đang trong stack</dd>
	<dt><b>`docker stack rm  STACK-NAME`</b></dt>
	<dd>Xoá 1 hay nhiều Stacks</dd>
	<dt><b>`docker stack services STACK-NAME`</b></dt>
	<dd>List danh sách các services trong stack</dd>
</dl>

---
Tags: [[DEV/Docker]]

