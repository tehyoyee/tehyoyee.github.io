---
layout: single
title: "born2beroot"
categories: linux
tag: debian, linux, virtual box
toc: true
author_profile: false
sidebar:
 nav: "docs"
---

## 데비안 (Debian)
<br>

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

## Virtual Machine

가상머신은 위험한 작업을 수행하기 용이. <br>
바이러스에 감염된 데이터에 엑세스하고 운영체제를 테스트할 수 있다.
가상 머신은 sandbox화되므로 가상머신내의 소프트웨어가 호스트 컴퓨터에 접근할 수 없다.
<br>
 - 하나의 컴퓨터에서 여러 운영 체제 환경을 실행할 수 있다.
 - 유지 및 관리 측면에서 효율적이다.

<br>
<br>

## Apt vs Aptitude

> 소프트웨어의 설치, 제거, 업데이트를 관리해주는 툴. <br>

### Apt (Advanced Packaging Tool)

- 오픈소스 소프트웨어
- 설치 및 삭제의 역할 (데비안을 위해 고안됨)
- CLI