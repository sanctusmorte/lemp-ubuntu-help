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
sudo mysql
exit

### Установка PHP
sudo apt install php-fpm php-mysql
