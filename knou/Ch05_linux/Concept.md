리눅스 시스템의 시작과 종료에 대해 마크다운으로 정리하겠습니다.

# 리눅스 시스템 시작과 종료

## 1. 운영체제의 부팅

### 부팅 과정
1. ROM BIOS
   - BIOS가 x86 시스템의 하드웨어 초기화
   
2. MBR (Master Boot Record)
   - GRUB 부트로더 실행
   
3. initramfs
   - `/boot/vmlinuz-<kernel-version>` 커널 이미지 로드
   - 초기 RAM 파일시스템 구성

4. 커널 실행
   - 하드웨어 감지, 드라이버 초기화
   - 루트(/) 파일시스템 마운트

5. systemd 실행
   - `/lib/systemd/systemd` 프로세스 시작
   - 시스템 초기화 담당

## 2. 초기화 데몬

### 초기화 시스템 종류
1. System V init
   - 전통적인 런레벨 기반 초기화 시스템

2. Upstart
   - Ubuntu 2006, RHEL 6에서 사용

3. systemd
   - 2011년 Fedora에서 시작
   - 현재 대부분의 리눅스 배포판이 채택
   - PID 1 프로세스로 실행

### systemd 유닛 타입
- `.service`: 서비스 유닛
- `.target`: 시스템 상태/런레벨
- `.device`: 장치 유닛
- `.mount`: 마운트 포인트
- `.socket`: 소켓 유닛
- `.path`: 경로 감시
- `.snapshot`: 시스템 스냅샷

### 런레벨과 타깃
| 런레벨 | 타깃 | 설명 |
|--------|------|------|
| 0 | poweroff.target | 시스템 종료 |
| 1 | rescue.target | 단일 사용자 모드 |
| 2-4 | multi-user.target | 다중 사용자 모드 |
| 5 | graphical.target | 그래픽 모드 |
| 6 | reboot.target | 재부팅 |

## 3. 시스템 종료

### 종료 명령어
```bash
systemctl halt      # 시스템 중지
systemctl poweroff  # 전원 끄기
systemctl reboot    # 재부팅
systemctl suspend   # 절전 모드
systemctl hibernate # 최대 절전 모드
```

### shutdown 명령
```bash
shutdown [options] time [message]
# 예시
shutdown -r +10    # 10분 후 재부팅
shutdown -h now    # 즉시 종료
shutdown -P +10    # 10분 후 전원 끄기
```

## 4. 데스크톱 환경

### 주요 데스크톱
1. GNOME
   - Red Hat 기본 데스크톱
   - 직관적인 사용자 인터페이스

2. KDE
   - MS Windows와 유사한 인터페이스
   - `yum -y groupinstall` 명령으로 설치 가능

### 시스템 관리
- 웹 콘솔(cockpit) 사용 가능
- `http://localhost:9090`으로 접근
- root 계정으로 로그인하여 시스템 관리 가능
