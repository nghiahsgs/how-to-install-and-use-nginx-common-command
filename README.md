# nginx-common-command
nginx common command

## Câu lệnh bật tắt
```
sudo systemctl status nginx
sudo systemctl stop nginx
sudo systemctl start nginx
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
