# Site Hosting

<!--toc:start-->
- [Site Hosting](#site-hosting)
    - [create nginx configuration](#create-nginx-configuration)
    - [add the following configuration](#add-the-following-configuration)
    - [enable site (creating a symbolic link)](#enable-site-creating-a-symbolic-link)
    - [test nginx configuration](#test-nginx-configuration)
    - [reload nginx](#reload-nginx)
    - [obtain ssl certificate with certbot](#obtain-ssl-certificate-with-certbot)
<!--toc:end-->

### create nginx configuration 
```
sudo vim /etc/nginx/sites-available/<site-name>
```

### add the following configuration
```
server {
  listen 80;
  server_name <site-name>-backend.amalitech-dev.net;
  
  root /var/www/example.com;
  index index.html;
  
  location / {
    proxy_pass http://localhost:<port>/;
  }
}
```

### enable site (creating a symbolic link)
```
sudo ln -s /etc/nginx/sites-available/<site-name> /etc/nginx/sites-enabled/
```

### test nginx configuration
```
sudo nginx -t
```

### reload nginx
```
sudo systemctl reload nginx
```
### obtain ssl certificate with certbot
```
sudo certbot --nginx
```
