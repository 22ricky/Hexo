---
title: Docker部署Gitlab
date: 2022-06-07 17:36:03
tags:
---
1. 拉取gitlab镜像
``` bash
docker pull gitlab/gitlab-ce:latest
```

2. 编写docker-compose.yml
``` yml
version: '3.8'
services:
  gitlab:
    image: 'gitlab/gitlab-ce:latest'
    container_name: gitlab
    restart: always
    environment:
      GITLAB_OMNIBUS_CONFIG: |
        external_url 'http://gitlab.example.com:8989'
        gitlab_rails['gitlab_shell_ssh_port'] = 2224
    ports:
      - '8989:8989'
      - '2224:2224'
    volumes:
      - './config:/etc/gitlab'
      - './logs:/var/log/gitlab'
      - './data:/var/opt/gitlab'
```

3. 启动gitlab容器
``` bash
docker-compose up -d
```

4. 查看``root``用户默认密码
``` bash
docker exec -it gitlab bash
cat /etc/gitlab/initial_root_password
```