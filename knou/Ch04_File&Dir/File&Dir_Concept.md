
# 파일과 디렉터리

## 1. 파일 시스템 탐색
#### 파일시스템
- 운영체제가 디스크 상에 파일들을 구성하는 방식
- 파일과 디렉터리의 집합을 구조적으로 관리하는 체계
- 리눅스는 전체 파일 시스템을 1개의 트리 구조로 관리
### 1.1 파일 시스템
- 루트 디렉터리 `/`
- 현재 작업 디렉터리 `.`

### 1.2 `ls` 명령
- `ls [options] [names]`
- `ls directory` , `ls file`
- 디렉터리 및 파일 목록 표시
- 옵션: `-a` (숨김 파일 포함), `-l` (자세한 정보), `-R` (하위 디렉터리 포함) 등

### 1.3 파일의 종류
- 일반 파일, 디렉터리, 링크, 소켓, 파이프, 문자 장치, 블록 장치 등

### 1.4 `file` 명령
- 파일의 종류 확인
`file /dev/sda1`
>여기서 sda는 디스크저장공간

### 1.5 `pwd` 명령
- 현재 작업 디렉터리 경로 확인

### 1.6 `cd` 명령
- 디렉터리 이동
- `cd [directory]`, `cd ..`, `cd /`, `cd -` 등

## 2. 파일과 디렉터리 관리
### 2.1 `mkdir` 명령
- 디렉터리 생성
- `mkdir [options] directories`
- `mkdir dir1 dir2 dir3`
- 옵션: `-p` (상위 디렉터리 자동 생성) 예시:`mkdir -p backup/java`
- `-m` (디렉터리 만들면서 권한 설정)

### 2.2 `rmdir` 명령
- 디렉터리 삭제
- `rmdir [options] directories`
- 옵션: `-p` (상위 디렉터리 삭제)

### 2.3 `cp` 명령
- 파일 복사
- `cp [options] file1 file2`
- `cp [options] files directory`
- 옵션: `-r` (디렉터리 복사)

### 2.4 `mv` 명령
- 파일 또는 디렉터리 이동/이름 변경
- `mv [options] source target`
- `mv [options] files directory`

### 2.5 `rm` 명령
- 파일 삭제
- `rm [options] files`
- 옵션: `-i` (확인 요청), `-r` (디렉터리 삭제), `-f` (강제 삭제)

### 2.6 파일/디렉터리 접근 권한
- 소유자(u), 그룹(g), 기타(o)
- 읽기(r), 쓰기(w), 실행(x)
- `chmod` 명령으로 권한 변경

### 2.7 `umask` 명령
- 새로 생성되는 파일/디렉터리의 초기 권한 설정

### 2.8 `chown` 명령
- 파일/디렉터리 소유자 변경

### 2.9 `ln` 명령
- 하드 링크와 심볼릭 링크 생성
- `ln [options] target [link_name]`

## 3. 파일의 내용 확인
### 3.1 `more` 명령
- 파일 내용 페이지 단위로 출력

### 3.2 `less` 명령
- `more` 명령과 유사, 추가 기능 제공

### 3.3 `head` 명령
- 파일의 처음 부분 출력
- `head [options] [files]`

### 3.4 `tail` 명령
- 파일의 마지막 부분 출력
- `tail [options] [files]`

### 3.5 `cat` 명령
- 파일 내용 출력 및 파일 병합
- `cat [options] [files]`

