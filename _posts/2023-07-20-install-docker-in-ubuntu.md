---
title: Ubuntu 22.04 LTS에서 docker 설치
date: 2023-07-20 14:20:00 +0900
categories: [개발환경, Ubuntu]
tags: [docker, ubuntu, 개발환경]
---

Ubuntu 22.04에서는 apt 소스 리스트에 docker가 포함되어 있지 않기 때문에 docker 공식 apt 저장소를 수동으로 추가하여 설치해야합니다.

## 1. 유효한 패키지 리스트 업데이트
```bash
sudo apt udpate
```

<br />

## 2. docker 공식 GPG키 추가
```bash
curl -s https://download.docker.com/linux/ubuntu/gpg | sudo gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/trusted.gpg.d/docker.gpg --import
```
> apt-key를 사용해도 되지만 deprecate 되었기 때문에, trusted.gpg.d 폴더에 직접 GPG키를 추가합니다.

<br />

## 3. docker 공식 apt 저장소 추가
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

<br />

## 4. 유효한 패키지 리스트 업데이트
```bash
sudo apt udpate
```

<br />

## 5. docker 설치
```bash
sudo apt install docker-ce docker-ce-li containerd.io
```

<br />

## 6. docker 설치 확인
```bash
sudo docker run hello-world
```
![docker result](/assets/img/posts/docker_install_result.png)


<br />
<br />

## Reference
전반적 과정 : <https://velog.io/@osk3856/Docker-Ubuntu-22.04-Docker-Installation>

trusted.gpg.d : <https://ko.linux-console.net/?p=8512#gsc.tab=0>