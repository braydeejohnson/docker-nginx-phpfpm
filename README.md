# docker-nginx-phpfpm
Nginx container to be used in conjunction with a [php-fpm container](https://hub.docker.com/r/braydeejohnson/phpfpm). This container is intended to wrap around a single `Laravel` based site.

The source for the containers can be found on [Github](https://github.com/braydeejohnson/docker-nginx-phpfpm)
The container builds can be found on [Docker Hub](https://hub.docker.com/r/braydeejohnson/nginx-phpfpm/)

Currently the latest tag is sufficient and works with multiple versions of PHP and PHP-FPM.

### Example docker-compose.yml
```
version: '2'
services:
  nginx:
    image: braydeejohnson/nginx-phpfpm
    links:
      - fpm
    volumes_from:
      - data
  fpm:
    image: braydeejohnson/phpfpm
    volumes_from:
      - data
  data:
    image: braydeejohnson/data
    volumes:
      - ./:/data/www
```

In order for nginx to properly serve to phpfpm you must name the service `fpm`, regardless of php-fpm version.

Feel free to submit a Pull Request or Issue at [my Github])(https://github.com/braydeejohnson/docker-nginx-phpfpm) if you would like to have this supported beyond its current capabilities.