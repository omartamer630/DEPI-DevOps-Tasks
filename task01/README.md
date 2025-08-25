# DEPI Task 1 

## Task Requirement

  1. Install Nginx && PHP
  2. Configure Nginx
  3. Connect Nginx with PHP by Socket and Port

---

### 1,2. Installation of Nginx && PHP

```bash
sudo apt update && apt install nginx php-fpm8.3
```

Check if Nginx & PHP are Downloaded
```bash
nginx -v

php-fpm8.3 -v
```
---

### 3. Configure Nginx with Socket and port

Nginx Default Configuration is set in `/etc/nginx/conf.d/`, So you will use one of the configuartions in this Task `php_port.conf` or `php_socket.conf` you can't use both, Using Socket is better because it is secured it use the Internal Communication, in the opposite the Port could be danger because the Attackers could find the network port that you opened and exploit it if firewarall aren't properly configued
