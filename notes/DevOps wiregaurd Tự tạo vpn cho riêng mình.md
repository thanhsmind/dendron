---
type: programing 
---
# DevOps wiregaurd Tự tạo vpn cho riêng mình 

Chạy lệnh và làm theo hướng dẫn sau để cài đặt thủ công Wireguard VPN:

> 1/ apt-get update && apt-get upgrade

2/ Tiếp theo, chúng ta cần kích hoạt Chuyển tiếp IP. Chuyển tiếp IP là khả năng hệ điều hành chấp nhận các gói mạng đến trên một giao diện, nhận biết rằng nó không dành cho bản thân hệ thống mà nó phải được truyền cho một mạng khác. Chỉnh sửa tệp /etc/sysctl.conf và thay đổi và bỏ ghi chú đến dòng có nội dung net.ipv4.ip_forward=1

> bằng cách: vim /etc/sysctl.conf hoặc sử dụng lệnh:

> echo -e '\n# Enable IP forwarding (routing) - WireGuard\nnet.ipv4.ip_forward = 1' >> /etc/sysctl.conf

> Sau đó chạy: sysctl -p để kích hoạt các thay đổi.

4/ apt install wireguard - để cài đặt WireGuard Server trên máy chủ đã mua

![](https://telegra.ph/file/e71cf4f002a34c74a7e50.png)

https://www.wireguard.com/

5/ cd /etc/wireguard. Sau đấy, tạo public và private keys cho client và sever: 

> KEY_NAME="client"

> wg genkey | tee ${KEY_NAME}-private.key | wg pubkey > ${KEY_NAME}-public.key

> KEY_NAME="server"

> wg genkey | tee ${KEY_NAME}-private.key | wg pubkey > ${KEY_NAME}-public.key

Chạy lần lượt các lệnh sau:

> cat server-private.key

SFBBN9P9DxL+7ANVylBNeIlJ5uVVUtSvknhivYn+XHQ=

  

> cat server-public.key

3JSddOplAdTXV6X9uRAYNdUqiXYXL6QIE6xN0Osz9mc=

  

> cat client-private.key

uN+eLnDwpAfSE2exaDHbcz/WGuqWIvHw3cWIcQHuk0M=

  

> cat client-public.key

cFQCrhL4vaGVrPnrU+opJNsaozLmMLXM60Ew0FwqB24=

ghi chú lại từng key trên notepad.

  

5/ chạy lệnh:

> ip route show | grep default

sau đấy lấy tên card mạng mặc định, Ubuntu thì card mạng mặc định là: eth0

kế đến tạo file conf wg0.conf: 

> vim /etc/wireguard/wg0.conf

với nội dung (để ý thay thếeth0 nếu tên card mạng của bạn khác nhé):

> [Interface]

> PrivateKey = server_private_key

> Address = 10.8.77.1/24

> SaveConfig = true

> ListenPort = 51820

> PostUp = /usr/sbin/iptables -A FORWARD -i wg0 -j ACCEPT; /usr/sbin/iptables -t nat -A POSTROUTING -s 10.8.77.0/24 -o eth0 -j MASQUERADE

> PostDown = /usr/sbin/iptables -D FORWARD -i wg0 -j ACCEPT; /usr/sbin/iptables -t nat -D POSTROUTING -s 10.8.77.0/24 -o eth0 -j MASQUERADE

>   

> [Peer]

> PublicKey = client_public_key

> AllowedIPs = 10.8.77.2 

  

Lưu ý: AllowedIPs phải tăng số theo số lượng client mà bạn có. Ví dụ 10.8.77.3, hoặc 10.8.77.4 và cứ tăng dần nhé. Tối đa là 10.8.77.254

Bước tiếp theo tạo file client.conf (dùng cho máy ngoài kết nối tới Wireguard server)

với nội dung file như sau:

> [Interface]

> PrivateKey = client_private_key

> Address = 10.8.77.2/24

> DNS = 1.1.1.1, 8.8.8.8

>   

> [Peer]

> PublicKey = server_public_key

> AllowedIPs = 0.0.0.0/0

> Endpoint = 128.199.70.5:51820

> PersistentKeepalive = 15

  

6/ Để kiểm tra xem máy chủ hoạt động chạy:

> wg-quick up wg0

Nếu bạn muốn wireguard tự hoạt động khi khởi động, bạn cần chạy

> systemctl enable wg-quick@wg0

Sau đó, bạn chạy lệnh:

> wg

để kiểm tra xem Wireguard server đã chạy OK chưa

> 7/ apt install qrencode - để tạo QR code cho điện thoại

> Upload file hình QR lên imgur.com hoặc lên trang cá nhân nào đó của bạn. Hoặc test nhanh thì dùng lệnh: python3 -m http.server

rồi sau đấy vào trình duyệt web đánh: http://ip_cua_server_wireguard:8000/hinhqr.png

8/ Tải Wireguard về điện thoại, có cả Iphone và các loại điện thoại HDH Android. Sau khi cấu hình được nhập hay scan mã QR, hãy đảm bảo bật Exclude private IPs nếu không bạn sẽ không thể truy cập các máy chủ mạng LAN (chỉ áp dụng cho nền tảng Android).


---
Tags: [[DevOps]] [[Computer Networking]] 