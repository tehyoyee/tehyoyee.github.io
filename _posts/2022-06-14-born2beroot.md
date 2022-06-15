---
layout: single
title: "born2beroot"
categories: linux
tag: debian, linux, virtual box, lvm, ssh, appArmor
toc: true
author_profile: false
sidebar:
 nav: "docs"
---





## 데비안 (Debian)

- 오픈소스 소프트웨어
- 데비안 GNU/리눅스 GNU/허드 GNU/NetBSD 등 있다.
- 정식판은 리눅스만 존재.

- 설치 및 업그레이드의 단순함.
- 패키지매니저 APT(Advansed Packing Tool)업데이트 방식으로 
- 다른 패키지와의 의존성확인, 보안관련업데이트 자동으로 설정 및 설치.

- 안정성과 보안에 중점.
- 여러가지 서버에 쓰일 수 있음. 우분투등 다른 리눅스의 기반.

- motto "The universal operation system"


- 데비안은 51000여 꾸러미를 갖춘 저장소를 관리한다.

기능 : 저장소. <br>
안정 : 안정성 검증을 마친 꾸러미를 저장하는 곳. 처음하는 사람에게 적합.<br>
백포트 : 일부 소프트웨어의 안정판보다 더 최신 판을 제공.  특정 소프트웨어의 최신 판을 원하는 사용자를 위함. <br>
시험 : 안정성을 시험하는 판을 저장. 새로운 버전을 시험할때 적합. <br>
불안정(unstable) : sid 로 불림. 개발하고 있는 꾸러미를 보관. <br>
<br>
<br>

## Centos (Community Enterprise Operation System)

<br>

- 리눅스 배포판중 하나. 
- RHEL의 최신버전을 포킹 한다.
- RHEL을 철저하게 반영.
- 장점 : 리눅스서버시장의 1인자인 RHEL을 무료로 이용.
- 카카오 네이버도 이걸 이용.
- CentOS 8 버전부터 stream버전만 지원. 무료장점 사라짐.
- 커뮤니티기반이기에. 사후관리가 없다.
- 전문인력이 아니라면 안정성문제가 생길 수 있음.
- RHEL업데이트되고 한두달 더 걸림.
- 이 공백을 매꿔줄 보안인력이 필요함.

> 인력이 충분한 일반소프트웨어기업은 CentOS <br>
은행같은 보안은 RHEL을 선호. <br>
한국어 지원이 미비하다.

<br><br>
___

## Virtual Machine

> 가상머신은 위험한 작업을 수행하기 용이. <br>
바이러스에 감염된 데이터에 엑세스하고 운영체제를 테스트할 수 있다.
가상 머신은 sandbox화되므로 가상머신내의 소프트웨어가 호스트 컴퓨터에 접근할 수 없다.<br>

 - 하나의 컴퓨터에서 여러 운영 체제 환경을 실행할 수 있다.
 - 유지 및 관리 측면에서 효율적이다.

<br>
<br>
___

## Apt vs Aptitude

> 소프트웨어의 설치, 제거, 업데이트를 관리해주는 툴. <br>
오픈소스 소프트웨어이고 데비안을 위해 고안되었다.

### Apt

- low-level package manager
- CLI
- 패키지 삭제시 사용되지않은 패키지를 삭제하려면 apt-get에서 `-auto-remove` 옵션이나 `apt-get autoremove`가 명시되어야한다

### Aptitude

- high-level interactive package manager
- Apt가 CLI인 반면에 UI가 제공된다
- why, why-not 커맨드로 특정 기능이 안되는 이유를 알려준다
- 패키지 삭제시 사용되지않은 패키지도 함께 삭제해준다

<br><br>
<br>

## AppArmor (Application Armor)

- 시스템관리자가 프로그램 프로필별 역량을 제한해주는 리눅스 커널 보안 모듈
- 리눅스 보안 모듈(LSM)에 의해 구현
- 강제적 접근 통제(MAC)를 제공하며 DAC또한 제공

```
dpkg -l apparmor
apt install apparmor
apt install apparmor-utils
```

<br>

### MAC (Mandatory Access Control)

> MAC는 관리자만이 사용자에게 자원에 대한 권한을 부여받는다. 관리자만이 객체에 대한 보안등급과 사용자의 보안등급을 관리할 수 있다. <br>

### DAC (Discretionary Access Control)

> DAC는 자원에 대한 접근권한을 사용자에 기반한다. 사용자나 그룹이 객체의 소유자일 때, 다른 사용자나 그룹에게 권한을 부여할 수 있다. 자원에 대한 소유권을 기반으로 작동<br>

### RABC (Role Based Access Control)

> 관리자가 사용자의 맡은 역할에 기반하여 권한을 부여한다.<br>

<br><br>
<br>

## LVM (Logical Volume Manager)

리눅스의 저장 공간을 효율적으로 관리하기위한 방법.

> 기존의 방식에서는 리눅스 내부의 하나의 디스크를 여러 파티션으로 나누어 각각의 디렉토리에 마운트한다. LVM에서는 파티션대신 볼륨의 개념으로 저장 공간을 관리한다. 물리적인 공간을 수정할 필요없이 각각의 파티션들에 대한 짜투리 공간을 묶어 사용할 수 있다. 또한, 하나의 파티션을 여러 볼륨으로 나누어 사용할 수 있다.<br>

### PV, PE, VG, LV, LE

> PV(Physical Volume)은 디스크의 물리적공간을 나타내고 PE(Physical Extent)는 그 안의 단위를 나타낸다 (4mb). 여러 PE에서 공간을 다시 만들어낸 것이 VG(Volume Group)이 되고, 이것은 필요에 따라 LV(Logical Volume)으로 나누어진다. LV의 내부 단위는 LE(Logical Extent). <br>

<br><br>
<br>


## UFW (Uncomplicate Firewall)

다양한 리눅스환경에서 사용되는 방화벽관리 프로그램으로 명령어와 사용법이 간단한 것이 특징. 

```
apt-get install ufw -y 
ufw status verbose 
ufw enable
ufw default deny    //incoming deny
ufw allow 4242         //ssh연결허용
ufw status verbose
ufw delete <규칙 번호>		// port 삭제
```

<br><br><br>

## SSH (Secure SHell)

네트워크 프로토콜중 하나로 호스트에 통신하기위해 사용되는 인터넷 프로토콜이다. 기존 유닉스시스템에서 사용하던 텔넷에 암호화기능을 추가하여 나온 프로토콜이다. 기본적으로 CLI에서 작업을 한다. 기본포트는 22.

### SSH Key

> 클라이언트는 Private Key와 Public Key를 생성한다. 통신하고자 하는 컴퓨터에 Public key를 저장하고 이는 암호화에 사용된다. 클라이언트는 접속요청을 받고 부여받은 public key가 private와 한쌍인지 확인한다. private key는 복호화에 사용된다. <br>

```
apt search openssh-server       // 설치 확인
apt install openssh-server
vim /etc/ssh/sshd_config 		// server측 설정  client는 ssh_config
#Port 22 -> Port 4242 로 변경
#PermitRootLogin prohibit-password -> PermitRootLogin no 로 변경	//root의 ssh 접근 제한
systemctl restart ssh 
systemctl status ssh        // ssh 실행여부 & port 확인

ssh <username>@<MAC_IP> -p <host port>
```

<br><br>
<br><br>

## sudo, user, group

sudo를 사용하여 사용자는 root의 권한을 이용할 수 있다. root의 비밀번호를 모르는 상태에서 관리권한을 부여할 수 있기 때문에 안전을 위하여 sudo를 사용.<br>

```
apt-get update
apt-get install sudo
dpkg -l sudo    // sudo 설치여부
visudo          // sudoer 파일 접근

id <user>		// user의 그룹 확인
passwd <user>	// user의 비밀번호 변경

groupadd <group>		// 그룹 추가
groupdel <group>		// 그룹 삭제
usermod -aG <group> <user>	// 사용자를 그룹에 추가
id <user>		// 사용자의 그룹확인
chage -L <user>		// 사용자의 비밀번호확인
```

<br><br><br>

## cron

유닉스 계열 기반 운영체제의 시간 기반 잡스케줄러이다. crontab 파일들에 규정된 명령어들을 기반으로 일정시간에 셸 명령어를 실행할 수 있다.<br>
http://www.cronmaker.com/<br>

```
* * * * * command	// * * * * * <=> m,h,d,m,w
- : 그 사이 값
, : 지정 값
/ : 특정 주기로 나누기
이용 가능.
ex ) /10 * * * * bash ~/monitoring.sh | wall		// 10분 단위
ex ) /1 * * * * bast ~/monitoring.sh | wall
	/1 * * * * sleep; bash ~/monitoring.sh | wall		// 30초 단위
```
```
systemctl status cron.service

```

<br><br><br>

## 비밀번호 정책 설정
```
vim /etc/login.defs
PASS_MAX_DAYS   30      // 패스워드 만료 30일
PASS_MIN_DATS   2       // 2일이후 패스워드 변경 가능
PASS_WARN_AGE   7       // 패스워드 만료 7일전 경고
```
```
apt-get -y install libpam-quality   // 패스워드 규칙 모듈
vim /etc/pam.d/common-password
password    requisite   pam-pwquality.so retry=3 minlen=10 ucredit=-1 lcredit=-1 dcredit=-1 maxrepeat=3 reject_username enforce_for_root difok=7
retry       최대 입력 횟수
minlen      최소길이
ucredit     대문자 갯수
lcredit     소문자 갯수
dcredit     숫자 갯수
maxrepeat   연속된 같은 문자 제한
reject_username     username 제한
enforce_for_root    root에게도 적용
difok       기존패스워드와 달라야하는 문자수
```

## hostname 변경

```
hostnamectl     //hostname 확인
hostnamectl set-hostname <hostname>     //hostname 변경

```