# Памятка LEMP Ubuntu 20.04 (настройка веб-сервера)

### Установка Nginx
sudo apt update <br/>
sudo apt install nginx

### Настройка брандмауэра ufw
sudo ufw app list <br/>
sudo ufw allow 'Nginx HTTP' <br/>
sudo ufw status
