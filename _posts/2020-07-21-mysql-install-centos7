---
layout: post
title: Centos7 Mysql 설치하기
subtitle: 
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---

## 1. rpm 레파지토리 다운로드 및 설치
```console
wget http://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
sudo rpm -ivh mysql80-community-release-el7-3.noarch.rpm
sudo yum -y install mysql-community-server
```

---

## 2. mysql 시작 및 설정

> ### 1. 비밀번호 암호화 방법 변경
* my.cnf 파일 default-authentication-plugin=mysql_native_password 주석 해제

> ### 2. 시작 및 상태 확인
```console
sudo systemctl start mysqld
sudo systemctl status mysqld
```

> ### 2. 서버 재부팅시에 자동으로 mysql 실행
```console
sudo systemctl enable mysqld
```
> ### 3. 임시번호를 알아둔다
```console
sudo cat /var/log/mysqld.log | grep -i "temporary password"
```
---

## 3. 계정 관리

> ### 1. 비밀번호 정책 확인 및 변경
```sql
SHOW VARIABLES LIKE 'validate_password%';
SET GLOBAL validate_password.policy=LOW;
```

> ### 2. root 비밀번호 변경 및 외부 접속 추가
```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'mysql12#$';
CREATE USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root12#$';
GRANT ALL PRIVILEGES ON *.* to 'root'@'%' WITH GRANT OPTION;
```

> ### 3. 계정 추가
```sql
create user 'peloton'@'%' identified by 'peloton12#$';
```
* 모든 IP대역에서 접근 가능한 유

> ### 4. 계정 권한 변경
```sql
GRANT ALL PRIVILEGES ON OPENKITCHEN.* TO 'peloton'@'%' WITH GRANT OPTION;
```
* peloton 계정으로 OpenKitchen의 모든 테이블에 모든 IP대역에서 접근 가능하도록 변경

---
