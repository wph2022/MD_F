1.安装docker
sudo apt  install docker.io 
sudo usermod -aG docker $USER

sudo reboot
docker 安装cloudflare
docker run -d --restart unless-stopped docker.wangdd.online/cloudflare/cloudflared:latest tunnel --no-autoupdate run --token eyJhIjoiZTk3ODUwMzQ0OTUyMmJlNDhkZjExZDkxZmRjZmNjNzMiLCJ0IjoiMGRlNDQwY2ItZmZiNy00MjRjLWFmMzktN2U1YWMyYWZmYmRjIiwicyI6IlpUWTRZbUl3T0dVdFkyWmxNQzAwTm1FekxUZ3dabVV0TmpGak9URTJZbU14TWpNMSJ9

docker run -d --restart always docker.wangdd.online/cloudflare/cloudflared:latest tunnel --no-autoupdate run --token eyJhIjoiZTk3ODUwMzQ0OTUyMmJlNDhkZjExZDkxZmRjZmNjNzMiLCJ0IjoiZTQxODQ2MjEtMWYwOC00YTc1LThlOTktNTI0NTYxMzQ5NjRkIiwicyI6Ill6VTFOelk0T0RrdFlXRTNaaTAwWkdZeUxXSmtZMll0TWpjd09HWmlZMll4WlRjNSJ9
2.cloudflared 下载地址:
https://github.com/cloudflare/cloudflared/releases/tag/2024.11.0
rdp:
cloudflared access rdp --hostname rdp.wangdd.sbs --url rdp://localhost:33890
Refer to SM8450/SM8475 LINUX ANDROID SOFTWARE USER GUIDE (SP80-PV345-4)

ssh
#-url localhost:222 的作用是转到本机器的222端口，方便用任意ssh工具连接管理
cloudflared access ssh --hostname ssh.wangdd.sbs -url localhost:222 

3.内网穿透:
https://blog.csdn.net/Tisfy/article/details/143114828

安装1pan1
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
