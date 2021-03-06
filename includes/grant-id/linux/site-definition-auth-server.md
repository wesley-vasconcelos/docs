﻿```nginx
server {
    listen        80;
    listen        443 ssl;  # comment if you don't have an SSL certificate yet

	# Replace with your base domain and your login domain
    server_name   id.patorum.com  login.id.patorum.com;

	# Path of the SSL certificate and key (comment if you don't have an SSL certificate yet)
    ssl_certificate      /etc/ssl/certs/grantid.pem;
    ssl_certificate_key  /etc/ssl/private/grantid.key;

    location / {
        proxy_pass         http://localhost:5011;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
        proxy_buffer_size       16k;
        proxy_busy_buffers_size 16k;
    }
}
```
