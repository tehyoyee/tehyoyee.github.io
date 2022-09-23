---
layout: single
title: "[42 Seoul] pipex"
categories: Linux
tag: 42seoul, Linux, shell
toc: true
author_profile: false
sidebar:
 nav: "docs"
---

<br>
<br>
<br>

### gettimeofday
```c
#include <sys/time.h>
#include <unistd.h>



struct timeval mytime;	//	timeval 인스턴스를 생성하고 사용한다.
```

```c
int gettimeofday(struct timeval *tv, struct timezone *tz);
int settimeofday(const struct timeval *tv ,  const  struct
             timezone *tz);
```
```c
struct timeval
{
    long tv_sec;       // sec
    long tv_usec;      // micro sec
}
```
```c
struct timezone
{
    int tz_minuteswest:  // 그리니치 서측분차  
    int tz_dsttime       // DST 보정타입(일광 절약시간)
}
```