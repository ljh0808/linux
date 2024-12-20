# 리눅스 텍스트 편집 요약

## 1. 리눅스 텍스트 편집기 종류
- **gedit**: GNOME용 GUI 편집기
- **emacs**: 확장성 높은 편집기
- **vi/vim**: 가장 기본적인 텍스트 편집기 (Vi Improved)

## 2. vi 편집기 기본 사용법

### 시작과 종료
```bash
vi [options] [filename]
# 예: vi -R test.txt (읽기전용)
# 예: vi +10 test.txt (10번째 줄부터 시작)
```

### 종료 명령어
- `ZZ` 또는 `:wq`: 저장 후 종료
- `:q`: 그냥 종료 (변경사항 없을 때)
- `:q!`: 강제 종료
- `:wq [filename]`: 다른 이름으로 저장 후 종료
- `:x`: 변경사항 있을 때만 저장 후 종료

## 3. vi의 주요 편집 명령어

### 입력 모드 전환
- `i`: 현재 커서 위치에서 입력
- `a`: 현재 커서 다음 위치에서 입력
- `o`: 현재 줄 아래에 새 줄 삽입
- `O`: 현재 줄 위에 새 줄 삽입

### 커서 이동
- `h, j, k, l`: 좌, 하, 상, 우 이동
- `w`: 다음 단어로
- `b`: 이전 단어로
- `0`: 줄 처음으로
- `$`: 줄 끝으로
- `G`: 파일 끝으로
- `nG`: n번째 줄로 이동

### 삭제 명령
- `x`: 한 문자 삭제
- `dw`: 단어 삭제
- `dd`: 현재 줄 삭제
- `ndd`: n줄 삭제

### 복사와 붙여넣기
- `yy`: 현재 줄 복사
- `nyy`: n줄 복사
- `p`: 커서 다음에 붙여넣기
- `P`: 커서 앞에 붙여넣기

### 검색과 치환
```
/pattern : 앞으로 검색
?pattern : 뒤로 검색
n : 다음 검색
N : 이전 검색
:s/old/new : 현재 줄에서 치환
:%s/old/new/g : 파일 전체에서 치환
```

## 4. 파일 찾기와 문자열 검색

### locate
- 데이터베이스에서 파일 빠르게 검색
- `updatedb` 명령으로 데이터베이스 갱신 필요
```bash
locate [options] pattern
```

### find
- 실시간 파일 검색
```bash
find [pathnames] [expression]
```
주요 옵션:
- `-name pattern`: 파일명으로 검색
- `-type`: 파일 타입으로 검색
- `-size`: 크기로 검색
- `-user`: 소유자로 검색
- `-exec command`: 검색 결과에 대해 명령 실행

### grep
- 파일 내용 검색
```bash
grep [options] pattern [files]
```
주요 옵션:
- `-r`: 하위 디렉토리 포함 검색
- `-i`: 대소문자 구분 없이 검색
- `-v`: 매치되지 않는 행 출력
- `-n`: 행 번호 표시
