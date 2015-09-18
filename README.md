# Docker container for Magento 2 (CentOS)

## How to use Docker container

- Execute command:

```
$ docker pull magento/centos:v1
```

- Then add virtual host to *hosts* file

```
127.0.0.1 magento2.docker.loc
```

- Launch container

```
$ docker run --cap-add=ALL -p 127.0.0.1:80:80 -e VIRTUAL_HOST=magento2.docker.loc -i -t magento/centos:v1 /bin/bash
```

- After container is launched, start services

```
$ service php-fpm start && service nginx start && service mysqld start && service varnish start
```

## How to build image

- Clone repository

- Clone Magento2 from repository [magento/magento2](https://github.com/magento/magento2)
and place it in a folder *\<path-to-repository-files\>/magento2*

- Run composer

- In console execute command for building Docker image

```
$ docker build -t <image-name>:<version> <path-to-repository-files>
```

- After build is complete, add virtual host to *hosts* file

```
127.0.0.1 magento2.docker.loc
```

- Launch container

```
$ docker run --cap-add=ALL -p 127.0.0.1:80:80 -e VIRTUAL_HOST=magento2.docker.loc -i -t <image-name>:<version> /bin/bash
```

- After container is launched, start services

```
$ service php-fpm start && service nginx start && service mysqld start && service varnish start
```

*This container is for testing use - not for production environment.*
