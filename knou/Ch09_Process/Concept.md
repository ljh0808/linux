# UNIX 시스템 09강 강의 요약

## 프로세스 정의 및 관리

### 프로세스 개요
- **프로세스 제어 블록(PCB)** 
  - 각 프로세스에 대한 정보 관리
  - PID(Process ID), PPID(Parent PID) 포함
  - UID, EUID, GID, EGID 등 권한 정보 저장
- **systemd가 PID 1을 담당**
- **bash는 기본 셸 프로세스**

### 프로세스 생성 메커니즘
- `fork()` 시스템 호출로 새 프로세스 생성
- `exec(program)` 호출로 새 프로그램 실행
- 예: `ls` 명령어 실행 과정
  - `fork()`: 부모 프로세스에서 자식 프로세스 생성
  - `exec(ls)`: ls 프로그램 실행

### 프로세스 실행 모드

#### 포어그라운드(Foreground) 프로세스
- 터미널에서 직접 실행되는 프로세스
- 키보드 제어 가능
- 단축키 
  - `Ctrl+C`: 프로세스 종료
  - `Ctrl+Z`: 프로세스 일시 중지

#### 백그라운드(Background) 프로세스
- `&` 기호로 실행
- 터미널에서 동시에 다른 작업 가능
- `jobs` 명령어로 백그라운드 작업 확인
- `fg`, `bg` 명령어로 작업 제어

### 특수 권한

#### SetUID
- 파일 실행 시 소유자 권한으로 실행
- `chmod 4755` 또는 `chmod u+s`로 설정
- 예: `/usr/bin/passwd`에 SetUID 설정

#### SetGID
- 그룹 권한으로 파일 실행
- `chmod 2775` 또는 `chmod g+s`로 설정

#### Sticky Bit
- 디렉토리의 파일 보호
- `chmod 1777` 또는 `chmod o+t`로 설정
- 예: `/tmp` 디렉토리에 Sticky Bit 설정

## 프로세스 상태 및 관리 도구

### 프로세스 상태 확인 명령어

#### ps 명령어
- 프로세스 정보 출력
- 주요 옵션:
  - `-ef`: 모든 프로세스 상세 정보
  - `-aux`: 사용자 지향 프로세스 정보
  - `--forest`: 프로세스 계층 구조 표시

#### top 명령어
- 실시간 시스템 리소스 및 프로세스 모니터링
- CPU, 메모리 사용량 확인
- 대화형 인터페이스로 프로세스 관리 가능

### 프로세스 제어 명령어

#### kill 명령어
- 프로세스에 시그널 전송
- 주요 시그널:
  1. HUP: 재시작
  2. INT: 인터럽트 (Ctrl+C)
  9. KILL: 강제 종료
  15. TERM: 정상 종료
  19. STOP: 프로세스 중지

#### nice/renice 명령어
- 프로세스 우선순위(Nice Value) 조정
- Nice Value 범위: -20(highest) ~ 19(lowest)

#### nohup 명령어
- 터미널 종료 후에도 프로세스 계속 실행
- 표준 출력을 `nohup.out`에 저장

## cron 서비스

### cron 개요
- 주기적인 작업 예약 및 자동 실행
- `/etc/crontab` 및 `/etc/cron.d/` 디렉토리 사용
- `crontab` 명령어로 사용자별 스케줄 관리

### crontab 파일 형식
- 5개 시간/날짜 필드: 분, 시, 일, 월, 요일
- 다양한 패턴 지원 (* , / - )
- 예: `0 */6 * * 1-5 root echo are | mail - jjpark@localhost`

### crontab 명령어
- `-l`: crontab 내용 확인
- `-e`: crontab 편집 (vi 사용)
- `-r`: crontab 삭제
- `-u`: 다른 사용자의 crontab 관리
