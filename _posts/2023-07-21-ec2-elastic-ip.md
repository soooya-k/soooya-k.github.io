---
title: EC2 인스턴스에 탄력적 IP(Elatic IP) 설정
date: 2023-07-21 19:21:00 +0900
categories: [AWS, EC2]
tags: [AWS, EC2, Elatic IP]
---

생성한 EC2 인스턴스는 재실행 때마다 임의의 퍼블릭 IP를 할당 받습니다.

EC2 인스턴스를 서버로 사용하기 위해서는 고정된 접속점을 갖는게 편리합니다.

EC2에서 제공하는 탄력적 IP를 사용하면 고정 IP를 할당 받을 수 있고,

이 IP를 EC2 인스턴스에 연결 할 수 있습니다.

<br />

## * 탄력적 IP (Elastic IP) 할당

### 1. EC2 콘솔에 접속합니다.

### 2. 좌측 메뉴에서 [네트워크 및 보안] - [탄력적 IP]를 클릭합니다.

![Alt text](/assets/img/posts/EIP_side_menu.png)

<br />

### 3. 우측 화면의 [탄력적 IP 주소 할당]을 클릭합니다.

![Alt text](/assets/img/posts/EIP_assign_eip.png)

<br />

### 4. 정보 입력

#### - 네트워크 경계 그룹

퍼블릭 IPv4 주소가 보급되는 영역의 논리적 그룹입니다.

입력창을 클릭하면 선택 가능한 그룹이 나타납니다.

![Alt text](/assets/img/posts/EIP_network_boundary_group.png)

<br />

### 5. [할당]을 클릭해서 탄력적 IP를 생성합니다.

생성된 후에 다시 탄력적 IP에 들어가보면 아래와 같이 IP가 생성되어 있습니다.

![Alt text](/assets/img/posts/EIP_assign_result.png)

<br />

> ## <span style="color:red"> ** !!! 주의 !!! ** </span>

탄력적 IP는 <span style="color:green">**사용 중**</span>에는 과금이 되지 않지만, 한정된 자원이기 때문에 할당만 받고 사용하지 않으면 과금이 됩니다.

여기서 <span style="color:green">**사용 중**</span>의 의미는 실행되고 있는 EC2 인스턴스에 연결된 상태를 말합니다.

EC2 인스턴스가 실행되고 있지 않으면 연결이 되어 있더라도 과금이 되기 때문에,

필요할 때 할당받아 연결해 사용하고, 그렇지 않을 때에는 반드시 <span style="color:red">**할당을 해제**</span>하면서 사용해야 합니다.


<br />
<br />

### 6. EC2 인스턴스에 연결

탄력적 IP 주소 목록에서 EC2 인스턴스에 연결하려는 IP를 선택합니다.

우측 상단의 [작업]을 클릭하고 [탄력적 IP 주소 연결]을 선택합니다.

![Alt text](/assets/img/posts/EIP_work_connect_EIP.png)

<br />

리소스 유형은 [인스턴스]를 선택하고, 생성되어 있는 인스턴스를 선택 한 후 [연결]을 눌러 연결합니다.

![Alt text](/assets/img/posts/EIP_connect.png)

<br />

EC2 인스턴스에 들어가서 퍼블릭 IP를 확인해보면 잘 연결 된 것을 볼 수 있습니다.

![Alt text](/assets/img/posts/EIP_EC2_public_ip.png)

<br />
<br />


## * 탄력적 IP 해제

탄력적 IP를 해제하기 위해서는 먼저 연결을 해제 해야합니다.

### 1. 탄력적 IP 주소 연결 해제

EC2 콘솔의 왼쪽 메뉴에서 [네트워크 및 보안] - [탄력적 IP]를 선택합니다.

연결 해제하려는 탄력적 IP 주소를 선택 한 후, [작업] - [탄력적 IP 주소 연결 해제]를 선택합니다.

![Alt text](/assets/img/posts/EIP_disconnect_EIP_address.png)

<br />

대화상자가 나타나면 [연결 해제]를 선택합니다.

![Alt text](/assets/img/posts/EIP_disconnect_EIP_address_dialog.png)

<br />

### 2. 탄력적 IP 해제

다시 해제하려는 탄력적 IP를 선택 한 후, [작업] - [탄력적 IP 주소 릴리스]를 선택합니다.

![Alt text](/assets/img/posts/EIP_work_eip_release.png)

<br />

릴리스 대화 상자의 [릴리스] 버튼을 누릅니다.

![Alt text](/assets/img/posts/EIP_release_dialog.png)

<br />

탄력적 IP 주소 목록에서 해당 IP가 사라진 걸 확인 할 수 있습니다.
