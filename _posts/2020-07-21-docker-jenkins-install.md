---
layout: post
title: Jenkins 설치하기
subtitle: Docker
cover-img: /assets/img/path.jpg
tags: [books, test]
comments: true
---

### 1. docker-compose.yml 작성 및 실행
```yml
jenkins:
    image: jenkins
    container_name: peloton_jenkins
    user: root
    restart: always
    volumes:
        - /home/peloton/docker/jenkins/jenkins_home:/var/jenkins_home
    environment:
        TZ: "Asia/Seoul"
    ports:
        - 8181:8080
```
```console
docker-compose up -d jenkins
```

---

### 2. Addministrator password 입력
*docker logs containerID > password 출력되면 웹에 입력

---

### 3. Install Suggest Plugins

---

---

## compose 없이 실행하는 방법

### 1. Jenkins Docker images 다운로드
    docker pull jenkins/jenkins:lts
    
---

### 2. Jenkins Docker 실행
```console
docker run -e TZ=Asia/Seoul -v /home/peloton/docker/jenkins/jenkins_home:/var/jenkins_home -d -p 8181:8080 --name peloton_jenkins -u root jenkins/jenkins:lts
```
*-d : detached mode 흔히 말하는 백그라운드 모드  
*-p : 호스트와 컨테이너의 포트를 연결 (포워딩)  
*-v : 호스트와 컨테이너의 디렉토리를 연결 (마운트)  
*–name : 컨테이너 이름 설정  
*-u 실행할 사용자 지정  
*맨 마지막 jenkins/jenkins:lts 는 실행할 이미지의 레포지토리 이름이며 만약 이미지가 없을 경우 이미지를 docker hub 에서 땡겨오므로 주의한다.  

---
