# docker-server
Quick development environment, which runs on Docker.

Contains latest versions of:
* php (with composer + hirak/prestissimo + sllh/composer-versions-check + nodejs)
* apache (a2enmod rewrite)
* mysql
* phpmyadmin

PHP extension enabled:
* mysqli
* gd
* zip
* intl
* bcmath

## Use
1. Run **build.sh** (This builds containers. You can run it only once.)
1. Run **up.sh** for start.
1. Run **exec.sh** if you want to do some stuff in a container.