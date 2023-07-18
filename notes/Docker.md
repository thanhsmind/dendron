---
type: programing 
---
# Docker

## Docker là gì?
_Docker là một dự án mã nguồn mở giúp tự động triển khai các ứng dụng Linux và Windows vào trong các container ảo hóa._

### Thành phần chính của Docker
- **Docker Engine**: Dùng để tạo các Docker image, chạy các Docker container
- **Docker Hub**: Lưu trữ lại các Docker Image

### Các khái niệm 
- **Docker Machine**: tạo ra các Docker engine trên máy chủ
- **Docker Compose**: chạy ứng dụng bằng cách định nghĩa cấu hình các Docker Container thông qua tệp cấu hình.
- **Docker Image**: 1 cách đóng gói cấu hình. Được tạo ra bởi Docker Engine, nội dung của Docker Image không bị thay đổi khi chuyển từ nơi này tới nơi khác. 
- **Docker Container**: runtime của Docker images, sử dụng để chạy ứng dụng

## [[Sự khác biệt giữa Docker & Hypervisors]]
![[docker-vs-hypervisors.png]]

**Hypervisor**: ảo hoá nằm ở tầng Hardware. **Docker** dùng chung Kernel với host, chạy độc lập trên Host Operating System. Docker chạy như 1 service trên máy chính, vì vậy tận dụng được sức mạnh của máy chủ. Hypervisor phải được phân chia về cấu hình ngay từ đầu, phải cài thêm Hệ điều hành dể quản lý, nên sẽ tốn tài nguyên hơn, khó mở rộng.

- https://docs.docker.com/get-started/orchestration/
- [[Docker Intall on Ubuntu]]
- [[Docker Swarm]]
- [[Docker Secret Manage sensitive data]]
- [[Docker config Manage non-sensitive data]]