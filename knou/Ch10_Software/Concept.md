
# 리눅스 소프트웨어 관리 요약

## 1. 패키지 관리 기본 개념
- 리눅스에서는 소프트웨어를 패키지 형태로 관리
- 주요 패키지 형식: DEB(.deb), RPM(.rpm)
- 패키지는 의존성 관리가 필요함

## 2. RPM(RPM Package Manager)
### 패키지 명명 규칙
`<이름>-<버전-릴리즈>.<아키텍처>.rpm`
예시: `firefox-102.8.0-2.el9_1.x86_64.rpm`

### 주요 RPM 명령어
```bash
rpm -i package_file    # 패키지 설치
rpm -e package_name    # 패키지 제거
rpm -qa               # 설치된 모든 패키지 조회
rpm -qi package_name  # 패키지 정보 조회
rpm -qf file         # 파일이 속한 패키지 찾기
rpm -ql package_name  # 패키지 파일 목록 보기
```

## 3. DNF(YUM 후속) 패키지 관리자
- YUM의 후속 버전으로, RPM 패키지 의존성을 자동으로 해결
- 설정 파일 위치: `/etc/dnf/dnf.conf`, `/etc/yum.repos.d/`

### 주요 DNF 명령어
```bash
dnf search string     # 패키지 검색
dnf install package   # 패키지 설치
dnf update           # 패키지 업데이트
dnf remove package   # 패키지 제거
dnf info package     # 패키지 정보 확인
dnf list installed   # 설치된 패키지 목록
```

## 4. 파일 압축
### gzip
```bash
gzip file           # 파일 압축 (.gz 생성)
gzip -d file.gz     # 압축 해제
gunzip file.gz      # 압축 해제
```

### bzip2
- gzip보다 높은 압축률 제공
```bash
bzip2 file          # 파일 압축 (.bz2 생성)
bzip2 -d file.bz2   # 압축 해제
bunzip2 file.bz2    # 압축 해제
```

### tar
```bash
tar cvf file.tar directory/   # 디렉토리 묶기
tar xvf file.tar             # tar 풀기
tar cvfz file.tar.gz dir/    # gzip으로 압축하며 묶기
tar xvfz file.tar.gz         # gzip 압축 해제하며 풀기
```

주요 tar 옵션:
- c: 새로운 묶음 생성
- x: 묶음 풀기
- v: 자세한 정보 출력
- f: 파일 이름 지정
- z: gzip 압축/해제
- j: bzip2 압축/해제
