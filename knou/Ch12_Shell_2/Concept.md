# 리눅스 셸 스크립트의 제어 구조

## 1. 선택 구조 (if와 case)

### if 명령문
```bash
if command; then
    command...
[ elif command; then
    command... ]
[ else
    command... ]
fi
```

- `if` 명령 후 세미콜론(;) 또는 개행 필수
- 명령의 종료 상태가 0이면 성공(참), 1이면 실패(거짓)

### test 명령
- 조건 검사를 위해 사용
- 문법: `test expression` 또는 `[ expression ]`

주요 테스트 연산자:
- 파일 테스트:
  - `-f file`: 일반 파일 여부
  - `-d file`: 디렉터리 여부
  - `-r file`: 읽기 권한 여부
  - `-s file`: 파일 크기가 0보다 큰지 여부

- 문자열 비교:
  - `string1 = string2`: 문자열 같음
  - `string1 != string2`: 문자열 다름
  
- 정수 비교:
  - `-eq`: 같음
  - `-ne`: 다름
  - `-lt`: 작음
  - `-gt`: 큼
  - `-le`: 작거나 같음

### case 명령문
```bash
case word in
    pattern1) commands;;
    pattern2) commands;;
    *) commands;;
esac
```

## 2. 반복 구조

### for 명령문
1. 리스트 반복
```bash
for variable in word...; do
    commands
done
```

2. C스타일 반복
```bash
for ((exp1; exp2; exp3)); do
    commands
done
```

### while 명령문
```bash
while command; do
    commands
done
```
- 조건이 참인 동안 반복 실행

### until 명령문
```bash
until command; do
    commands
done
```
- 조건이 참이 될 때까지 반복 실행
- while의 반대 개념

## 주요 특징
- `break`: 반복문 탈출
- `continue`: 현재 반복 건너뛰기
- 산술 연산: `$[expression]` 또는 `$((expression))`
- `let` 명령어로 산술 연산 가능: `let a=a+1`

이러한 제어 구조들을 활용하여 더 복잡한 셸 스크립트를 작성할 수 있다.
