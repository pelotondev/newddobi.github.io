---
layout: post
title: Redis 명령어
subtitle: 
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---

## 참고
* https://redis.io/commands
* https://medium.com/garimoo/%EB%A0%88%EB%94%94%EC%8A%A4-acl-7dc10b1b7acb

---

### 계정 생성
```console
ACL SETUSER peloton on >변경할비밀번호 allcommands allkeys
```

---

### 계정 삭제
```console
ACL DELUSER peloton
```

---

### 계정 확인
```console
ACL LIST
```

---
