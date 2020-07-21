---
layout: post
title: Docker 설치하기
subtitle: Centos7
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---

## 1. yum으로 docker 레파지토리 추가하고 설치하기
```console
yum install -y yum-utils device-mapper-persistent-data lvm2
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install -y docker-ce
```  

# 2. 실행

    systemctl start docker


# 3. docker 설치 후 /var/run/docker.sock의 permission denied 발생하는 경우

    sudo chmod 666 /var/run/docker.sock


# 4. docker-compose 설치

    sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compos
