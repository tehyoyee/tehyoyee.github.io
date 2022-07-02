---
layout: single
title: "[Linux] fd_redirection"
categories: Linux
tag: redirection, fd
toc: true
author_profile: false
sidebar:
 nav: "docs"
---


### dup2

```c
#include <unistd.h>
int dup2(int oldfd, int newfd);
```

oldfd를 복제하여 newfd에 할당한다.<br>
newfd be allocated the lowest fd that was unused in calling process.<br>
they share file offset, file status flags.

## File Descriptor의 redirection

```c
#include <unistd.h>
#include <fcntl.h>

int main(int ac, char *av, char **envp)
{
	int fd1 = open("a.txt", O_WRONLY);
	int fd2 = open("b.txt", O_CREAT | O_WRONLY | O_TRUNC);

	char *str[2];
	str[0] = "cat";
	str[1] = NULL;
	dup2(fd1, 0);
	dup2(fd2, 1);
	execve("/bin/ls", str, envp);
}
```
dup2를 이용하여 stdin의 input의 방향을 fd1의 파일로 지정하고, 
stdout을 fd2의 파일로 지정한다. 이후 execve함수를 이용하여 cat명령어를 실행하게 되면 a.txt의 내용이 b.txt에 복제된다.