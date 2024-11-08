# UNIX 시스템 - 5강 요약

## 운영체제의 부팅
1. ROM BIOS
2. MBR(Master Boot Record)
   - GRUB(Grand Unified Bootloader)
3. initramfs
   - `/boot/vmlinuz-<kernel-version>`
   - initramfs
4. 커널의 실행
   - 장치 드라이버 로드
   - 루트 파일시스템 마운트
5. systemd 프로세스 실행
   - `/lib/systemd/systemd`

## 초기화 데몬
- System V init
- Upstart (Ubuntu 2006, RHEL 6)
- systemd (2011 Fedora, RHEL 7, SUSE, Ubuntu 16.04)

## systemd 프로세스
- PID 1 프로세스
- 다양한 유닛 타입 관리
  - service, target, device, mount, path, socket, snapshot 등

## 런레벨 및 타깃
- 0-6번 런레벨에 해당하는 타깃 유닛
- `systemctl get-default`, `systemctl set-default <name.target>` 명령 사용

## systemctl 명령
- `start`, `stop`, `reload`, `restart`, `status`, `enable`, `disable`, `is-active`, `is-enabled` 등
- 서비스 관리를 위한 다양한 옵션 제공

## 시스템 종료
- `systemctl halt`, `systemctl poweroff`, `systemctl reboot` 등의 명령 사용
- `shutdown` 명령으로 종료 시간 지정 가능

## 데스크톱
- GUI 기반 운영체제 (X, GNOME, KDE 등)
- `yum -y groupinstall GNOME` 등으로 데스크톱 환경 설치 가능

추가 정보:
- systemd 프로세스의 세부적인 유닛 타입과 설정 파일 위치에 대한 설명이 더 필요할 수 있습니다.
- 데스크톱 환경 선택과 관련된 추가 정보를 제공할 수 있습니다.
