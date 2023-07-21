---
title: SSH 접속 시 pem 파일 bad permissions 오류.
date: 2023-07-21 10:00:00 +0900
categories: [문제 해결, AWS]
tags: [문제 해결, AWS, EC2, SSH]
---

<br />

## 문제

SSH client를 사용하여 EC2의 인스턴스에 접속 시,

사용하는 프라이빗 키 파일의 권한이 너무 open되어 있으면 bad permissions 오류가 발생합니다.

```
Bad permissions. Try removing permissions for user: NT AUTHORITY\\Authenticated Users (S-1-5-11) on file D:/001_MyFolder/aws/ec2-test.pem.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions for 'D:\\001_MyFolder\\aws\\ec2-test.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "D:\\001_MyFolder\\aws\\ec2-test.pem": bad permissions
ubuntu@15.164.154.183: Permission denied (publickey).
```

<br />
<br />

## 해결

### 1. 리눅스 계열
chmod를 사용하여 간단하게 권한 조정이 가능합니다.
```bash
$ chmod 400 [프라이빗 키 파일 경로]
```

예)
```bash
$ chmod 400 ./ec2-ubuntu-22_04.pem
```

<br />


### 2. Windows

Windows의 경우 아래와 같은 과정으로 권한 조정이 가능합니다.

<br />

### 2-1. 탐색기 - 프라이빗 키 파일에서 우클릭 - 속성 - 보안

### 2-2. [고급]

![Alt text](/assets/img/posts/pem_permission_01.png)

<br />

### 2-3. [상속 사용 안 함]

![Alt text](/assets/img/posts/pem_permission_02.png)

<br />

### 2-4. 이 개체에서 상속된 사용 권한을 모두 제거합니다.

![Alt text](/assets/img/posts/pem_permission_03.png)

<br />

### 2-5. [추가]

![Alt text](/assets/img/posts/pem_permission_04.png)

<br />

### 2-6. [보안 주체 선택]

![Alt text](/assets/img/posts/pem_permission_05.png)

<br />

### 2-7. Windows 계정 입력 후 [이름 확인] - [확인]

![Alt text](/assets/img/posts/pem_permission_06.png)

<br />

### 2-8. 기본 권한 확인 후 [확인]

![Alt text](/assets/img/posts/pem_permission_07.png)

<br />

### 2-9. 완료.
