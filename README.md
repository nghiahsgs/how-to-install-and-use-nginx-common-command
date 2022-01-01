# how-to-install-and-use-nginx-common-command
how-to-install-and-use-nginx-common-command

## install nginx ubuntu
```
sudo apt install nginx
```
## install nginx centos
```
sudo dnf install nginx
sudo systemctl enable nginx
sudo systemctl start nginx
```
```
sudo firewall-cmd --permanent --zone=public --add-service=https --add-service=http
sudo firewall-cmd --reload
```


## Câu lệnh bật tắt
```
sudo systemctl status nginx
sudo systemctl stop nginx
sudo systemctl start nginx
```

if err: nginx: [emerg] bind() to [::]:80 failed (98: Unknown error)
```
sudo apachectl stop
```

Nhan tiện lưu ké câu lệnh apache 2
```
sudo /etc/init.d/apache2 restart
```

## deploy app flask sử dụng nginx
Thêm 1 cấu hình web , cài bằng nginx
```
sudo apt install nginx
sudo rm /etc/nginx/sites-enabled/default
sudo nano /etc/nginx/sites-enabled/flaskblog
```

Trong file flaskblog vừa tạo thêm nội dung như sau:
```
server {
  listen 80;
  server_name your_ip;
  location /static {
    alias /home/.../static
  }
  location / {
    proxy_pass http://localhost:8000;
    include /etc/nginx/proxy_params;
    proxy_redirect off;
  }
}

```

Sau khi thay đổi xong thì restart nginx
```
sudo systemctl restart nginx
```
