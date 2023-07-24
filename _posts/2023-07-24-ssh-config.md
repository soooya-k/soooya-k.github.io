---
title: OpenSSH client 설정
date: 2023-07-24 12:22:00 +0900
categories: [개발 환경, SSH]
tags: [SSH]
---

Windows 기준 OpenSSH client의 설정 파일은 아래 경로에 위치합니다.

```
Windows 계정 사용자 폴더\.ssh\config
```

<br />

## 접속 정보 저장

```
Host [구분 이름]
HostName [접속 IP 및 domain]
User [login ID]
IdentityFile [프라이빗 키 파일(pem)]
```

예)
```
Host ec2-server
HostName 12.34.56.78
User ubuntu
IdentityFile D:\ec2-ubuntu-22_04.pem
```

사용)
```
> ssh ec2-server
```

