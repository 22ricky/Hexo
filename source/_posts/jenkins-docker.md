---
title: Docker部署Jenkins
date: 2022-06-08 00:47:44
categories: Docker
tags:
---
### 拉取jenkins镜像
``` bash
docker pull jenkins/jenkins:2.332.3-lts
```

### 编写docker-compose.yml
``` yml
version: '3.8'
services:
  jenkins:
    image: 'jenkins/jenkins:2.332.3-lts'
    container_name: jenkins
    ports:
      - '8080:8080'
      - '50000:50000'
    volumes:
      - './data/:/var/jenkins_home/'
```

### 启动jenkins容器
``` bash
docker-compose up -d
```

### 设置``data``数据卷权限重启
``` bash
chmod -R 777 data
docker-compose restart
```

### 查看jenkins密码
``` bash
docker logs -f jenkins
```