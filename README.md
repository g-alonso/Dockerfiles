# Dockerfiles
My dockerfiles 

## Create images

### Ubuntu 14.04
`docker build -t galonso/ubuntu:14.04 ./ubuntu`

## Apache 2.4.18
`docker build -t galonso/apache:2.4.18 ./apache`

## PHP 7.0.4
`docker build -t galonso/php:7.0.4 ./php7`

## Run PHP 7.0.4
`docker run -p 8080:8080 -v /home/dvlp/yourapp:/www/htdocs -v /path/to/httpd.conf:/www galonso/php:7.0.4`

## Virtual Host

```
<VirtualHost *:8080> 
    ServerName yourapp.dev
    DocumentRoot /www/htdocs/public
    <Directory /www/htdocs/public>
        Options +Indexes +FollowSymLinks +MultiViews
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>`
```
