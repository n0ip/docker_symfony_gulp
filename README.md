# Docker Symfony Gulp NodeJS correct permissions
Solved permissions problem

## How to install?
1. Install docker and docker-compose https://docs.docker.com/engine/installation/linux/ubuntulinux/
1. create your own .env file
Get your current UID and GUID:
Run in your terminal: `id -g` to get current GUID
`id -u` to get current UID
2. docker-compose up
3. look at ./docker/docker/ dir for small automatization scripts

Nginx, php-fpm and nodejs are running under www-data:www-data user, which uid is simular to your current user id.


