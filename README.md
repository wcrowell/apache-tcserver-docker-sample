# apache-tcserver-docker-sample

- docker sample 
- apache(mod_jk) => pivotal tcserver
- This is not JetBrains TeamCity 

## dependencies

- docker
- docker-compose

Adapted from: https://github.com/maeharin/apache-tomcat-docker-sample

## how to use

```
$ docker-compose build 
$ docker-compose up
```

then, access browser

- http://localhost/
- http://localhost/manager

## tips

```
$ docker exec -it httpd-container /bin/bash
$ docker exec -it tomcat-container /bin/bash
```
