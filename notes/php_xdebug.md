# php xdebug
## How to Install
[Xdebug: Documentation » Installation](https://xdebug.org/docs/install)
### Install xDebug in Alpine docker

```php
FROM wordpress:php7.1-fpm-alpine

RUN apk add --no-cache $PHPIZE_DEPS \
    && pecl install xdebug-2.5.0 \
    && docker-php-ext-enable xdebug
```

### Install xDebug in Alpine docker

```php
pecl install xdebug-2.5.0 

docker-php-ext-enable xdebug
```

### Recheck xDebug installed
```php
php -i | grep Xdebug
```

### View folder settings
```
/usr/local/etc/php/conf.d/
```
## Enable Profiling
```
xdebug.remote_enable=1
xdebug.remote_autostart=1
;xdebug.remote_handler=dbgp
#To activate XDEBUG remote host must be your local IP address.
#This is not Docker machine ip address, but the ones running Phpstorm
xdebug.remote_host=host.docker.internal
xdebug.remote_port=9001
```
[PHPStorm + Xdebug + Alpine on Docker - DEV Community](https://dev.to/oranges13/phpstorm-xdebug-alpine-on-docker-13ff)
