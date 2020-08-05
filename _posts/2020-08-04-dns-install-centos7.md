---
layout: post
title: Centos7 DNS 사용하기
subtitle: 
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---


## 1. bind 설치
```console
sudo yum install -y bind bind-utils bind-chroot
```
---------------------------------------------------------------------------
## 2. 설정
* ### 1. /etc/named.conf 파일 수정
  + listen-on port 53 { 127.0.0.1; }; > listen-on port 53 { any; };
+ allow-query     { localhost; }; > allow-query     { any; };
+ recursion yes; > recursion no;
+ 추가

zone "pelotonkorea.com" IN {
        type master; file "pelotonkorea.com.zone";
        allow-update { none; };
};
> ### 2. /var/named/chroot/var/named/pelotonkorea.com.zone 파일 생성
>> ```shell
$TTL 1D
@       IN      SOA     ns.pelotonkorea.com. root.pelotonkorea.com. (
                                        20200805        ;serial
                                        86400           ;refresh
                                        15M     ;retry
                                        48H     ;expire
                                        86400 ) ;minimum
;

        IN      NS      ns.pelotonkorea.com.    ;primary dns
        IN      A       119.192.148.203         ;ip address
www     IN      A       119.192.148.203         ;www
*       IN      A       119.192.148.203         ;subdomain
```
>> 파일 작성 정상 확인
>> named-checkconf /etc/named.conf
>> named-checkzone pelotonkorea.com /var/named/chroot/var/named/pelotonkorea.com.zone
> ### 3. naemd-chroot 사용을 위한 파일 이동
```console
cp -p *.* ./chroot/var/named/.
```
> ### 4. named 실행 및 상태확인
```console
systemctl start named-chroot
systemctm status named-chroot
```
