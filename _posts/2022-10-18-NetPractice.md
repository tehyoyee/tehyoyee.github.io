---
layout: single
title: "[42 Seoul] NetPractice"
categories: Network
tag: 42seoul, network
toc: true
author_profile: false
sidebar:
 nav: "docs"
---

단말기, terminal은 네트워크망에서 이동하는 데이터를 사용하는 가장 말단의 기계를 의미한다. 네트워크에서는 End-point로 지칭함.
특정기기를 식별하기위해 주어진 고유값을 ip라고 함.
32비트를 8비트씩 쪼개서 43억개의 ip값을 얻을 수 있다.
그러나 ip값이 부족해져서 서브넷마스크를 만들게 되었다.
서브넷마스크란 host주소와 network주소를 나누는 것으로 255.255.255.0 or /0으로 표기한다.

네트워크 주소 = 하나의 로컬네트워크 주소
호스트 주소 = 로컬네트워크내의 단말기

서브넷 마스크 : 0비트는 호스트 1비트는 네트워크   32비트숫자로 ip를 마스킹함

123.123.123.14

123.123.123 = 네트워크주소
14 = 네트워크에 연결된 기기

