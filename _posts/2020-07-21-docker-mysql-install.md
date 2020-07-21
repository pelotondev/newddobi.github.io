---
layout: post
title: Docker Mysql 설치하기
subtitle: 
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---

### 1. docker-compose.yml 작성 및 실행
```yml
  mysql:
      image: mysql
      container_name: peloton_mysql
      command: --default-authentication-plugin=mysql_native_password
      restart: always
      environment:
        MYSQL_ROOT_PASSWORD: root1234
      ports:
          - 3306:3306
```
```console
docker-compose up -d mysql
```

---

### 2. 계정 추가
```sql
create user 'peloton'@'%' identified by 'peloton12#$';
```  
> 모든 IP대역에서 접근 가능한 유저

---

### 3. 계정 권한 변경
```sql
GRANT ALL PRIVILEGES ON OpenKitchen.* TO 'peloton'@'%' WITH GRANT OPTION;
```  
> peloton 계정으로 OpenKitchen의 모든 테이블에 모든 IP대역에서 접근 가능하도록 변경
