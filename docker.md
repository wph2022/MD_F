### 1.安装docker
sudo apt  install docker.io 
sudo usermod -aG docker $USER

sudo reboot
### 2.docker 安装cloudflare
docker run -d --restart always docker.wangdd.online/cloudflare/cloudflared:latest tunnel --no-autoupdate run --token eyJhIjoiZTk3ODUwMzQ0OTUyMmJlNDhkZjExZDkxZmRjZmNjNzMiLCJ0IjoiZTQxODQ2MjEtMWYwOC00YTc1LThlOTktNTI0NTYxMzQ5NjRkIiwicyI6Ill6VTFOelk0T0RrdFlXRTNaaTAwWkdZeUxXSmtZMll0TWpjd09HWmlZMll4WlRjNSJ9
### 3.cloudflared 下载地址:
https://github.com/cloudflare/cloudflared/releases/tag/2024.11.0
rdp:
cloudflared access rdp --hostname rdp.wangdd.sbs --url rdp://localhost:33890
Refer to SM8450/SM8475 LINUX ANDROID SOFTWARE USER GUIDE (SP80-PV345-4)

### 4.ssh
#-url localhost:222 的作用是转到本机器的222端口，方便用任意ssh工具连接管理
cloudflared access ssh --hostname ssh.wangdd.sbs -url localhost:222 

### 5.内网穿透:
https://blog.csdn.net/Tisfy/article/details/143114828

### 6.安装1pan1
docker run -d \
    --name 1panel \
    --restart always \
    --network host \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /var/lib/docker/volumes:/var/lib/docker/volumes \
    -v /opt:/opt \
    -v /root:/root \
    -e TZ=Asia/Shanghai \
    moelin/1panel:latest

	docker run -d 
    --name 1panel 
    --restart always 
    --network host 
    -v /var/run/docker.sock:/var/run/docker.sock 
    -v /var/lib/docker/volumes:/var/lib/docker/volumes 
    -v /opt:/opt 
    -v /root:/root 
    -e TZ=Asia/Shanghai 
    moelin/1panel:latest

1panel_password

sudo adduser --password docker docker
