# 리눅스 파일 시스템 관리 요약

## 1. 마운트(Mount)와 언마운트(Unmount)

### /etc/fstab 파일
- 시스템 시작 시 자동으로 마운트할 파일 시스템 정보 저장
- 주요 필드:
  - 장치명(/dev/sda1) 또는 UUID
  - 마운트 포인트
  - 파일시스템 종류
  - 마운트 옵션
  - dump 옵션 (0 또는 1)
  - fsck 순서 (0: 검사안함, 1: 루트, 2: 나머지)

### mount 명령어
```bash
# 기본 문법
mount [options] device directory

# 예시
mount -t ext4 /dev/sdb1 /mnt/data1
mount -t iso9660 -o ro /dev/sr0 /media/cd
```

### umount 명령어
```bash
umount device|directory
```

## 2. 파티션 관리

### 파티션 개념
- 물리적 디스크를 논리적으로 분할한 영역
- SCSI 디스크: /dev/sda, /dev/sdb 등
- 파티션: /dev/sda1, /dev/sda2 등

### 파티션 관리 도구
- **fdisk**: MBR 파티션 테이블용
- **parted**: MBR/GPT 모두 지원
- **gdisk**: GPT 전용
- **gparted**: GUI 버전

## 3. LVM(논리 볼륨 관리)

### 주요 개념
- **PV(Physical Volume)**: 물리적 볼륨
- **VG(Volume Group)**: 볼륨 그룹
- **LV(Logical Volume)**: 논리 볼륨

### 주요 명령어
```bash
# 물리 볼륨 생성
pvcreate /dev/sdb2

# 볼륨 그룹 생성
vgcreate volumeGroup /dev/sdb2 /dev/sdb3

# 논리 볼륨 생성
lvcreate -n volumeName -L size volumeGroup
```

## 4. 파일 시스템

### 주요 파일시스템 종류
- **ext4**: 리눅스 기본 파일시스템
- **XFS**: 대용량 파일시스템에 적합
- **Btrfs**: 차세대 리눅스 파일시스템
- **vfat**: USB 등 호환용
- **iso9660**: CD-ROM 용

### 파일시스템 관리 명령어

#### mkfs (파일시스템 생성)
```bash
mkfs -t ext4 /dev/devicename
```

#### fsck (파일시스템 검사)
```bash
fsck [options] device
```

#### df (디스크 사용량 확인)
```bash
df -h  # 사람이 읽기 쉬운 형태로 출력
df -T  # 파일시스템 타입 포함
```

#### du (디렉토리 사용량 확인)
```bash
du -sh directory  # 특정 디렉토리 총 사용량
du --max-depth=1 /home  # 홈 디렉토리 직계 하위 사용량
```

### 스왑(Swap) 관리
```bash
# 스왑 영역 생성
mkswap device

# 스왑 활성화
swapon device

# 스왑 사용량 확인
free
```
