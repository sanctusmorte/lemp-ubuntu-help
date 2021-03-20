# Памятка LEMP Ubuntu 20.04 (настройка веб-сервера)

### Установка Nginx
sudo apt update <br/>
sudo apt install nginx

### Настройка брандмауэра ufw
sudo ufw app list <br/>
sudo ufw allow 'Nginx HTTP' <br/>
sudo ufw status

### Узнать IP сервера VPS
curl -4 icanhazip.com

### Установка MySQL
sudo apt install mysql-server <br/>
sudo mysql_secure_installation <br/>
sudo mysql <br/>
exit

### Установка PHP
sudo apt install php-fpm php-mysql

### Настройка Nginx для использования процессора PHP
sudo mkdir /var/www/<b>your_domain</b> <br/>
sudo chown -R $USER:$USER /var/www/<b>your_domain</b> <br/>
sudo nano /etc/nginx/sites-available/<b>your_domain</b> <br/>
```
server {
    listen 80;
    server_name your_domain www.your_domain;
    root /var/www/your_domain;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```

* Вместо "your_domain" указываем название нашего домена (например - "<span style="color:red;">"example.com"</span>, <b>без "https://" или "http://"</b>) или IP адрес нашего сервера (например - 45.61.48.152)

sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/ <br/>
sudo nginx -t <br/>
sudo systemctl reload nginx <br/>
nano /var/www/your_domain/index.php <br/>
```
<?php
phpinfo();
```
### Настройка MySQL
sudo mysql <br/>
CREATE DATABASE <b>example_database</b>; <br/>
CREATE USER <b>'example_user'</b>@'%' IDENTIFIED WITH mysql_native_password BY <b>'password'</b>; <br/>
GRANT ALL ON <b>example_database</b>.* TO '<b>example_user</b>'@'%'; <br/>
exit <br/>
SHOW DATABASES; <br/>




