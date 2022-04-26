---
layout: single
title: "File Discriptor"
categories: Linux
tag: read, open, fcntl, file descriptor, open_max 
toc: true
author_profile: false
sidebar:
 nav: "docs"
---
<br>

## 개념

<br>

유닉스 시스템에서의 모든 객체는 파일이라 명명한다. 파일에 접근하기위해서 부여하는 음이 아닌 정수값을 *File Disciptor*(이하 fd)라고 부른다. 파일 오픈시에 커널에서는 global file table에 entry를 만들고 이 fd값을 반환한다. 시스템콜이 발생할 때 사용된다.<br>
fd는 global file table을 레퍼런스한다. 이는 inode table, data stream, byte offset과 같은  정보들을 포함한다.
<br>
<br>
### FD의 디폴트 값 (0, 1, 2)
|FD|Name|Abbreviation|
|--|--|--|
|0|Standard Input|stdin|
|1|Standard Output|stdout|
|2|Standard Error|stderr|

<br>
<br><br>

## open()

<br>
file control에 사용되는 헤더이다. open관련 함수를 사용할 수 있다.

```c
#include <fcntl.h>

int open (const char *FILENAME, int FLAGS[, mode_t MODE];
```

**OPTION**

|FLAGS|Desciption|
|--|--|
|O_RDONLY|읽기전용|
|O_WRONLY|쓰기전용|
|O_RDWR|읽기쓰기전용|
|O_CREAT|해당파일이 없다면 생성|
|O_EXCL O_CREAT|없는 파일이면 만들고 존재하면 error|
|O_TRUNC|파일내용 삭제|

<br><br>
<br>

## read()

<br>

```c
#include <unistd.h>

ssize_t read(int fd, void *buff, size_t nbytes);
```

<br>

fd참조하여 buff에 nbytes만큼의 값을 저장.
return : 글자수. 실패시 -1

<br><br><br>


## OPEN_MAX

<br>

fd의 최댓값을 나타낸다. <limits.h>에 정의되어있다. 각 OS마다 다르다.

Terminal에서 OPEN_MAX 값 확인

```
getconf OPEN_MAX
```

