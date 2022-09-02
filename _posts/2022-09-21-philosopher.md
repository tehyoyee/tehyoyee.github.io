---
layout: single
title: "[42 Seoul] philosopher"
categories: Linux
tag: 42seoul, Linux, shell
toc: true
author_profile: false
sidebar:
 nav: "docs"
---


<br><br><br>

```c
#include <pthread.h>
int	pthread_create(pthread_t *thread, const pthread_attr_t *attr, void *(*start_routine) (void *), void *arg);
int	pthread_detach(pthread_t thread);
int	pthread_join(pthread_t thread, void **value ptr);
int	pthread_mutex_init(pthread_mutex_t *mutex, const pthread mutexattr_t *attr);
int	pthread_mutex_destroy(pthread_mutex_t *mutex);
int	pthread_mutex_lock(pthread_mutex_t *mutex);
int	pthread_mutex_unlock(pthread_mutex_t *mutex);
```


### pthread_create

```c
int	pthread_create(pthread_t *thread, const pthread_attr_t *attr, void *(*start_routine) (void *), void *arg);
```

<br>
호출되는 프로세스에서 새로운 쓰레드를 생성.<br>
스레드 속성 객체 attr의 속성에 맞게 쓰레드를 생성한다.<br>
NULL값이라면 기본 스레드속성.<br>
thread에 thread id가 저장된다.<br>
생선된 쓰레드는 arg인자를 가지고 start_routine을 실행한다.<br>
<br>
<br>
<br>

### 임계 역역 (Critical Section)

임계영역이란 하나의 스레드만이 진입해야하는 특정 코드구역을 지칭한다.
공유자원의 변경이 일어날 수 있는 곳이 임계구역에 해당된다.

<br><br>

### Mutex (Mutual Exclusion) (상호 배제)

특정 쓰레드에 단독으로 들어가야하는 코드구역에서 동기화를 위해 사용되는 방법이다.

```c
#include <pthread.h>
#include <stdio.h>

int cnt;


< Mutex 예제 >
void *thread(void *vargp)
{
  cnt = 0;
  for (int i = 0; i < 10; i++)
    printf("%d\n", cnt++);
  return (0);
}

int main()
{
  pthread_t tid_1, tid_2;
  pthread_create(&tid_1, NULL, thread, NULL);
  pthread_create(&tid_2, NULL, thread, NULL);
  pthread_join(tid_1, NULL);
  pthread_join(tid_2, NULL);
}
```
위와 같은 코드 실행시 공유자원인 cnt를 계속 늘려 0~18까지 출력이 된다.<br>

```c
#include <pthread.h>
#include <stdio.h>

int cnt;
pthread_mutex_t mutex;

void *thread(void *vargp)
{
  pthread_mutex_lock(&mutex);
  cnt = 0;
  for (int i = 0; i < 10; i++)
    printf("%d\n", cnt++);
  pthread_mutex_unlock(&mutex);

  return (0);
}

int main()
{
  pthread_t tid_1, tid_2;
  pthread_mutex_init(&mutex, NULL);
  pthread_create(&tid_1, NULL, thread, NULL);
  pthread_create(&tid_2, NULL, thread, NULL);
  pthread_join(tid_1, NULL);
  pthread_join(tid_2, NULL);
}
```

위의 코드는 mutex를 사용하여 공유자원에 제한적으로 접근하게 하여
0~9가 2번출력된다.

<br>

```c
int pthread_mutex_init(pthread_mutex_t *mutex, const pthread_mutexattr_t *attr);
	//	attr의 속성인 뮤텍스를 초기화한다. attr은 기본적으로  NULL
```

<br>

```c
int pthread_mutex_lock(pthread_mutex_t *mutex);
	//	임계구역에 들어갈 때 뮤텍스를 잠근다.
```

```c
int pthread_mutex_unlock(pthread_mutex_t *mutex);
    //	임계구역에서 나올 때 뮤텍스 객체의 잠금을 해지한다.
```

```c
int pthread_mutex_destroy(pthread_mutex_t *mutex);
     뮤텍스 객체를 파괴한다.
```

```c
int pthread_detach(pthread_t thread);
    인자 thread를 커널에서 분리 시킨다. 분리된 스레드는 수행을 종료 시키고, 할당된 자원을 회수한다.
```