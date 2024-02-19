# Bài tập KTPM tuần 1 (INT3105_1)
Sinh viên: Ngô Hoàng Duy - 21020293
# 1. Docker, Docker-compose là gì ?
## Docker
- Docker là một nền tảng cho developers và sysadmin để develop, deploy và run application với container. Nó cho phép tạo các môi trường độc lập và tách biệt để khởi chạy và phát triển ứng dụng và môi trường này được gọi là container. Khi cần deploy lên bất kỳ server nào chỉ cần run container của Docker thì application của bạn sẽ được khởi chạy ngay lập tức.
- Docker tạo môi trường ảo dựa trên tài nguyên (CPU, RAM, ...) và thư viện hay kernel của máy host. Trong khi đó, máy ảo tuy có sử dụng tài nguyên chung với máy host nhưng thư viện hay kernel lại dùng độc lập. Do đó các container có thể build và loại bỏ nhanh hơn máy ảo.
## Docker-compose
- Docker Compose là một công cụ giúp quản lý các container Docker trong một ứng dụng. Docker Compose cho phép bạn sử dụng một file YAML duy nhất để có thể config các services cho application của bạn.
- Ngoài ra Docker compose còn có thể quản lý volume (lưu trữ), network giữa các container hay biến môi trường.
# 2. Linux vs Unix vs BSD vs *nix ? macOS thuộc loại nào
## Unix
- Unix là một họ hệ điều hành máy tính đa năng được viết vào những năm 1960 tại Bell Labs bởi một nhóm các nhà khoa học. Ban đầu, hệ điều hành này chỉ được sử dụng trong hệ thống Bell của AT&T.
- Hệ điều hành này Unix được tạo thành từ ba phần: Kernel, Shell và Program
## Linux
- Linux là một hệ điều hành mã nguồn mở phổ biến được phát triển dựa trên hệ điều hành Unix
- Linux không phải là một hệ điều hành hoàn chỉnh, Linux chỉ là một hạt nhân(kernal).
- Bản phân phối Linux phải làm công việc tập hợp tất cả các phần mềm cần thiết để tạo ra một hệ điều hành Linux hoàn chỉnh và kết hợp nó thành một bản phân phối Linux như Ubuntu, Mint, Debian, Fedora, Red Hat, hoặc Arch. Do đó, có rất nhiều bản phân phối Linux khác nhau.
## BSD
- BSD (Berkeley Software Distribution) là một phiên bản của Unix được phát triển tại Đại học California, Berkeley..
- BSD là mã nguồn mở và là một hệ điều hành hoàn chỉnh
- Có 3 hệ điều hành BSD chủ yếu: FreeBSD, NetBSD, OpenBSD. Trong đó FreeBSD là BSD phổ biến nhất, hướng tới hiệu suất cao và dễ sử dụng
## *nix
- *nix là một thuật ngữ tổng quát được sử dụng để chỉ tất cả các hệ điều hành dựa trên Unix, bao gồm Unix, Linux, BSD và cả macOS. Thuật ngữ này được sử dụng để chỉ một nhóm rộng lớn các hệ điều hành có nguồn gốc từ Unix, mà không cần phải liệt kê tất cả chúng một cách cụ thể.
## MacOS
- macOS, cái tên xuất phát từ cụm từ Macintosh operating system, là hệ điều hành do Apple phát triển, và được giới thiệu lần đầu vào năm 2001.
- macOS được xây dựng trên một nền tảng gọi là Darwin, một dự án mã nguồn mở dựa trên BSD.
- macOS cung cấp một giao diện đẹp đẽ với nhiều tính năng cao cấp. Ngoài ra macOS còn có tính bảo mật cao
# 3. Alpine VS Ubuntu
- Alpine Linux là một hệ điều hành Linux nhẹ nhàng, bảo mật và dễ sử dụng. Nó được thiết kế để tối ưu hóa hiệu suất và bảo mật, với kích thước cài đặt cơ bản rất nhỏ, chỉ khoảng 5MB.
- Ubuntu là một hệ điều hành mã nguồn mở dựa trên Debian GNU/Linux.
## Khác nhau:
- Alpine sử dụng musl libc và busybox nên có kích thước rất nhỏ chỉ khoảng 5MB. Do sử dụng musl libc thay vì glibc (thư viện C phổ biến trong nhiều hệ điều hành Linux khác), dẫn đến một số phần mềm có thể không tương thích với Alpine Linux
- Ubuntu sử dụng glibc và nhiều package khác nên kích thước lớn hơn rất nhiều so với Alpine
- Ubuntu có giao diện thân thiện và dễ sử dụng. Ngoài ra Ubuntu có một cộng đồng người dùng và nhà phát triển lớn, cung cấp nhiều tài liệu hỗ trợ và hướng dẫn
# VNC
- VNC (Virtual Network Computing) là công nghệ giúp điều khiển máy tính từ xa (tác dụng như TeamView). Có thể truy cập máy tính từ xa, chia sẻ màn hình, điều khiển chuột, bàn phím.
- VNC có thể hoạt động trên nhiều hệ điều hành, bao gồm Windows, macOS, Linux và nhiều hệ điều hành di động.
- VNC có thể chậm hơn so với một số giải pháp truy cập từ xa khác, đặc biệt là khi mạng chậm hoặc không ổn định.
- VNC hoạt động trên một mô hình client / server. 
# Demo VNC
## Cài đặt Desktop Environment xfce thông qua Docker và VNC
B1: Cài đặt VNC Server, Desktop environment xfce thông qua Docker
- Pull image ubuntu:
```docker pull ubuntu:latest```
- Chạy image ubuntu:
```docker run -it --name vnc-xfce -p 5901:5901 -e USER=admin ubuntu:latest```
- Cài các package cần thiết:
```apt update -y && apt install vim xfce4 xfce4-goodies tightvncserver -y```
- Khởi tạo VNC server và đặt password. Ví dụ duyngo03
```vncserver```
- Config VNC server:
```
vncserver -kill :1
mv ~/.vnc/xstartup ~/.vnc/xstartup.bak
vim ~/.vnc/xstartup
```
- Nhập nội dung sau vào file ~/.vnc/xstartup
```
xrdb $HOME/.Xresources
startxfce4 &
```
- Sau khi nhập xong thì out file bằng lệnh ```:wq```
- Cấp quyền thực thi cho file xstartup
```
chmod 777 ~/.vnc/xstartup
```
- Khởi động lại VNC server, sử dụng tham số ```-geometry``` để cấu hình độ phân giải màn hình
```
vncserver -geometry 1920x1080 :1
```
B2: Cài đặt VNC Viewer và mở trên cổng ```127.0.0.1:5901```
Hình ảnh sau khi chạy thành công 
![image](https://github.com/duyngo03/INT3105_1/assets/100525536/eeb8c520-fa94-4d8d-9ef8-3fc75af7f27e)

