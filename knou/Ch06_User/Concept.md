# 리눅스 사용자 관리 요약

## 1. 사용자 계정 관련 주요 명령어

### su (Switch User)
- `su [-[l]] [username]`: 다른 사용자로 전환
- `su -l username` 또는 `su - username`: 로그인 셸과 환경으로 전환
- `su -c 'command'`: root 권한으로 단일 명령어 실행

### sudo
- 일시적으로 root 권한 획득
- 설정파일: `/etc/sudoers` (visudo로 편집)
- 기본 형식: `sudo [-u username] command`

## 2. 사용자 계정 관리

### useradd - 사용자 생성
```bash
useradd [options] username
```
주요 옵션:
- `-d`: 홈 디렉토리 지정
- `-e`: 계정 만료일 설정
- `-g`: 기본 그룹 지정
- `-G`: 보조 그룹 지정
- `-s`: 기본 셸 지정
- `-u`: UID 지정

### usermod - 사용자 정보 수정
주요 옵션:
- `-d`: 홈 디렉토리 변경
- `-l`: 로그인 이름 변경
- `-u`: UID 변경
- `-g`: 그룹 변경
- `-L`: 계정 잠금
- `-U`: 계정 잠금 해제

### userdel - 사용자 삭제
```bash
userdel [options] username
```
- `-r`: 홈 디렉토리와 메일 스풀 함께 삭제

## 3. 주요 설정 파일

### /etc/passwd
- 사용자 계정 정보 저장
- 형식: `username:x:UID:GID:설명:홈디렉토리:기본셸`

### /etc/shadow
- 암호화된 패스워드 정보 저장
- 패스워드 에이징 정보 포함

### /etc/login.defs
- 사용자 계정 생성 시 기본 설정
- UID/GID 범위, 패스워드 정책 등 정의

## 4. 그룹 관리

### 주요 명령어
- `groupadd`: 그룹 생성
- `groupmod`: 그룹 정보 수정
- `groupdel`: 그룹 삭제
- `gpasswd`: 그룹 암호 및 관리자 설정

### /etc/group
- 그룹 정보 저장
- 형식: `그룹명:x:GID:구성원목록`

## 5. 패스워드 관리

### chage - 패스워드 에이징 관리
```bash
chage [options] username
```
주요 옵션:
- `-l`: 패스워드 에이징 정보 확인
- `-d`: 마지막 변경일 설정
- `-E`: 계정 만료일 설정
- `-M`: 최대 사용 기간 설정
- `-m`: 최소 사용 기간 설정

