---
type: devops
---

# K8s Volume


## Types of Volumes
### local
`local` volume là mount thẳng tới disk, partition, directory của device.

`local` chỉ sử dụng như static PersistentVolume. Không hỗ trợ Dynamic provisioning. `local` volumes sử dụng ổn định lâu dài hơn `hostPath` không phải manual schedungling tới pods.

Problem: Điểm bất lợi của `local` là nếu node có vấn đề, có thể mất toàn bộ dữ liệu. Khả năng mất dữ liệu phụ thuộc vào chất lượng của ổ đĩa.



---
Ref:
- https://kubernetes.io/docs/concepts/storage/volumes/