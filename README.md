# NGINX & PHP Docker images

#### Exemplo de build para as imagens:

```
$ cd Nginx
$ docker build -t eduardoleal/nginx .
```


#### Exemplo de uso com docker-compose
  ```
  web:
      image: eduardoleal/nginx
      links:
          - php:php
      container_name: "nginx"
      volumes_from:
          - data
      volumes:
          - ./nginx-vhost.conf:/etc/nginx/sites-enabled/default
  php:
      image: eduardoleal/php56
      container_name: "php"
      external_links:
          - mysql57:mysqlserver
      volumes_from:
          - data
  data:
      container_name: "data"
      image: phusion/baseimage
      volumes:
          - ~/Code:/var/www
  ```
