# DEPI Task 1 

## Task Requirement

  1. Install Nginx && PHP
  2. Configure Nginx
  3. Connect Nginx with PHP by Socket and Port

---

### 1. Installation of Nginx && PHP

```bash
sudo apt update && apt install nginx php-fpm8.3
```

Check if Nginx & PHP are Downloaded
```bash
nginx -v

php-fpm8.3 -v
```
---

### 2. Configure Nginx with Socket and port

Nginx Default Configuration is set in `/etc/nginx/conf.d/`, So you will use one of the configuartions in this Task `/nginx_php_configuration/php_port.conf` or `/nginx_php_configuration/php_socket.conf` you can't use both, Using Socket is better because it is secured it use the Internal Communication, in the opposite the Port could be danger because the Attackers could find the network port that you opened and exploit it if firewarall aren't properly configued

and the different in the two configurations is this line:
```bash
        fastcgi_pass unix:/run/php/php8.3-fpm.sock;
```
this is for socket configuration you tell nginx use unix filesystem to find the PHP

in port configuration:
```bash
        fastcgi_pass 127.0.0.1:9000;
```
this is for port configuration you tell nginx to use the exposed port to find php

after choosing your way of connection you have to Reload and check nginx Syntax by:
```bash
sudo systemctl restart nginx

nginx -t
```

---

### 3. Configure Nginx with Socket and port

After Choosing your way of configuration you have to configure PHP to communicate as Socket or Port, By default it uses Socket.

To configure php you have to go to `/etc/php/8.3/fpm/pool.d/www.conf` and find `listen = /run/php/php8.3-fpm.sock` and comment it -> `;listen = /run/php/php8.3-fpm.sock`, and the put this -> `listen = 127.0.0.1:9000`

after configuring PHP you have to restart the PHP service:
```bash
sudo systemctl restart php8.3-fpm
```
