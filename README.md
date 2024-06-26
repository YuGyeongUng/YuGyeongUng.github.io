# 리눅스 명령어 조사: `top`, `ps`, `jobs`, `kill`

리눅스 명령어 `top`, `ps`, `jobs`, `kill`는 시스템 관리와 프로세스 관리를 위해 자주 사용되는 명령어들입니다. 각각의 명령어에 대한 설명은 다음과 같습니다:

## 1. `top`
`top` 명령어는 시스템의 현재 상태를 실시간으로 모니터링하는 데 사용됩니다. CPU 사용량, 메모리 사용량, 프로세스 목록 등을 실시간으로 보여줍니다.

- **주요 옵션 및 기능:**
  - `-d` : 화면을 업데이트하는 간격을 설정합니다. 예: `top -d 5` (5초마다 업데이트)
  - `-p` : 특정 PID를 모니터링합니다. 예: `top -p 1234`
  - `-u` : 특정 사용자의 프로세스를 보여줍니다. 예: `top -u username`

* 시스템에서 프로세스 목록을 <span style="color:red">cpu 사용량</span> 이 높은 것부터 보여주는 명령어
* 시스템 프로세스와 메모리 사용 상태를 3초간격으로 업데이트하여 출력

* 실행 전 옵션
  *     -b : 순간의 정보를 출력(배치 모드)
  *     -n [num] : top 실행 주기를 num번 만큼 설정
  *     -p [pid]: process ID의 정보만을 출력
 
* 실행 후 옵션
  *  shift + p : cpu 사용률 내림차순
  *  shift + m : 메모리 사용률 내림차순
  *  shift + t : 프로세스가 실행되고 있는 시간 순서(시행된 시간이 큰 순서)
  *  k : 프로세스 종료

<img src="https://t1.daumcdn.net/cfile/tistory/99285B3F5B14C72B1E">

- **사용 예시:**
  ```sh
  top

---

## 2. `ps`
`ps` 명령어는 현재 실행 중인 프로세스의 상태를 보여줍니다. 정적인 프로세스 정보를 제공하며, 다양한 옵션을 통해 필요한 정보를 필터링할 수 있습니다.

- **주요 옵션 및 기능:**

  - `-e` 또는 `-A` : 모든 프로세스를 보여줍니다.
  - `-f` : 풀 포맷으로 출력합니다.
  - `-u` : 특정 사용자의 프로세스를 보여줍니다. 예: ps -u username
  - `-p` : 특정 PID를 가진 프로세스를 보여줍니다. 예: ps -p 1234
  - `aux` : BSD 스타일 포맷으로 모든 프로세스를 보여줍니다. 예: ps aux

>ps -e | grep abc

<img src="https://search.pstatic.net/common/?src=http%3A%2F%2Fcafefiles.naver.net%2FMjAyMDAzMTZfMTkw%2FMDAxNTg0MzE2Nzc5MTg4.YN2FwvuzTyJ5BZlikCUndSsmTmkKvrq1dy615VM0S3og.vtZr0oBdu28NwNbUBsekGfGDH4qD1Cx0qWI-65yixFwg.PNG%2Fps.PNG&type=sc960_832">


- **사용 예시:**
  ```sh
  ps aux
  ps -ef

---

## 3. `jobs`
`jobs` 명령어는 현재 셸 세션에서 실행 중이거나 일시 중지된 백그라운드 작업을 보여줍니다. 주로 & 연산자와 함께 사용되는 백그라운드 작업을 관리합니다.

- **주요 옵션 및 기능:**

  - `-l` : 각 작업의 프로세스 그룹 ID를 포함하여 출력합니다.
  - `-p` : 각 작업의 프로세스 ID만 출력합니다.
  - `-r` : 현재 실행 중인 작업만 보여줍니다.
  - `-s` : 일시 중지된 작업만 보여줍니다.

> jobs [option] [작업번호]

|출력 결과| |
|:---:|:---:|
|running|작업이 계속 진행|
|done|작업이 완료되어 0을 반환|
|stopped|작업이 일시 중단|


- **사용 예시:**
  ```sh
  jobs
  jobs -l

---
  
## 4. `kill`
`kill` 명령어는 프로세스를 종료시키는 데 사용됩니다. 일반적으로 PID와 함께 사용되며, 다양한 시그널을 보낼 수 있습니다.

- **주요 옵션 및 기능:**

  - `-l` : 사용할 수 있는 시그널 목록을 보여줍니다.
  - `-s` : 특정 시그널을 보냅니다. 기본 시그널은 TERM입니다.
  - `-9` : 강제 종료 시그널 (SIGKILL)을 보냅니다. 예: kill -9 1234

> kill [option] [pid]
> kill ps -ef | grep 프로세스이름 | grep -v grep | awk '{print $2}’

- **사용 예시:**
  '''sh
  kill 1234
  kill -9 1234
  kill -s HUP 1234

---

## 요약
  - `top` : 실시간 시스템 모니터링
  - `ps` : 프로세스 상태 조회
  - `jobs` : 백그라운드 작업 관리
  - `kill` : 프로세스 종료

