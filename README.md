# docker-app
php:8.1-fpm
nginx:alpine
postgres:11.1-alpine

## Xdebug
To setting xdebug, change `xdebug.client_host` in the docker/build/xdebug.ini file on ip docker. To get docker ip
address use command `ifconfig` and copy ip under headline "docker0".
