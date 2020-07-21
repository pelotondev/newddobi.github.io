---
layout: post
title: Centos7 Redis 설치하기
subtitle: 
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---

## 1. REMI repository 추가 및 설치
```console
sudo yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
sudo yum --enablerepo=remi install redis
```

---

## 2. redis 실행 및 설정

> ### 1. 실행
```console
sudo systemctl enable --now redis
```
* enable --now > 실행하고, 재부팅 시 자동실행하도록 등록

> ### 2. 설정, 재시작 및 상태 확인
```console
sudo vim /etc/redis.conf > requirepass 설정
sudo systemctl restart redis
sudo systemctl status redis 
```

---
