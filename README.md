# Python 학습 샘플 코드 모음

이 폴더에는 Python 기초 학습을 위한 샘플 코드와 중학교 기술교과 성적 생성 프로그램이 포함되어 있습니다.

## 📚 Python 기초 학습 샘플 (5개)

### 1. 변수와 데이터 타입 (`01_variables_and_data_types.py`)
Python의 기본 데이터 타입과 변수 사용법을 학습합니다.

**학습 내용:**
- 변수 선언 (문자열, 정수, 실수, 불린)
- 데이터 타입 확인 (`type()` 함수)
- 타입 변환 (Type Conversion)
- 여러 변수 동시 선언
- 상수 표기 관례

**실행 방법:**
```bash
python 01_variables_and_data_types.py
```

---

### 2. 리스트와 반복문 (`02_lists_and_loops.py`)
리스트 자료구조와 다양한 반복문 사용법을 학습합니다.

**학습 내용:**
- 리스트 생성 및 인덱싱
- 리스트 메서드 (`append`, `insert`, `remove`, `len`)
- `for` 반복문과 `range()` 함수
- `while` 반복문
- 리스트 컴프리헨션
- `enumerate()` 함수 활용

**실행 방법:**
```bash
python 02_lists_and_loops.py
```

---

### 3. 함수와 모듈 (`03_functions_and_modules.py`)
함수 정의 및 모듈 사용법을 학습합니다.

**학습 내용:**
- 기본 함수 정의 및 호출
- 반환값이 있는 함수
- 기본 매개변수 (Default Parameters)
- 가변 인자 (`*args`, `**kwargs`)
- 람다 함수 (Lambda Function)
- 내장 함수 활용 (`max`, `min`, `sum`, `sorted`)
- `map`, `filter` 함수
- 재귀 함수 (Recursive Function)
- 모듈 import (`math`, `random`, `datetime`)

**실행 방법:**
```bash
python 03_functions_and_modules.py
```

---

### 4. 딕셔너리와 조건문 (`04_dictionaries_and_conditionals.py`)
딕셔너리 자료구조와 조건문 사용법을 학습합니다.

**학습 내용:**
- 딕셔너리 생성 및 접근
- 딕셔너리 수정 및 추가
- 딕셔너리 메서드 (`keys()`, `values()`, `items()`)
- 딕셔너리 반복문
- `if-elif-else` 조건문
- 복합 조건문 (`and`, `or`, `not`)
- `in` 연산자
- 중첩 딕셔너리 (Nested Dictionary)
- 삼항 연산자 (Ternary Operator)
- 딕셔너리 컴프리헨션

**실행 방법:**
```bash
python 04_dictionaries_and_conditionals.py
```

---

### 5. 파일 처리와 예외 처리 (`05_file_handling_and_exceptions.py`)
파일 입출력과 예외 처리 방법을 학습합니다.

**학습 내용:**
- 파일 쓰기 (`write`)
- 파일 읽기 (`read`, 한 줄씩 읽기)
- 파일에 추가하기 (`append`)
- 리스트를 파일로 저장/읽기
- `try-except` 예외 처리
- 파일 처리 예외 처리 (`FileNotFoundError`)
- `finally` 절 사용
- 사용자 정의 예외
- CSV 형식 데이터 저장
- 파일 존재 여부 확인 (`os.path.exists()`)

**실행 방법:**
```bash
python 05_file_handling_and_exceptions.py
```

**생성되는 파일:**
- `sample_data.txt`
- `students.txt`
- `students.csv`
- `nonexistent_file.txt`

---

## 🎓 중학교 기술교과 성적 생성기 (`middle_school_tech_scores.py`)

중학교 1학년 기술교과 성적 데이터를 자동으로 생성하는 프로그램입니다.

### 프로그램 개요

**성적 구성:**
- 기말고사: 60점 만점
- 수행평가 1: 15점 만점
- 수행평가 2: 15점 만점
- 수행평가 3: 10점 만점
- **총점: 100점 만점**

**데이터 규모:**
- 5개 반
- 각 반 30명
- **총 150명**

### 등급 체계 (상대평가)

전체 학생을 총점 기준으로 정렬한 후, 순위에 따라 등급을 부여합니다.

| 등급 | 비율 | 인원 | 설명 |
|------|------|------|------|
| **A** | 상위 20% | 30명 | 최우수 |
| **B** | 상위 21~50% | 45명 | 우수 |
| **C** | 상위 51~80% | 45명 | 보통 |
| **D** | 상위 81~95% | 22명 | 미흡 |
| **E** | 하위 5% | 8명 | 매우 미흡 |

### 주요 기능

1. **랜덤 학생 이름 생성**
   - 한국 성씨와 이름 조합
   - 남학생/여학생 이름 구분

2. **정규분포 기반 점수 생성**
   - 현실적인 점수 분포
   - 평가별 난이도 조절 가능

3. **상대평가 등급 계산**
   - 전체 학생 총점 기준 정렬
   - 순위에 따른 등급 자동 부여

4. **CSV 파일 저장**
   - `tech_scores.csv` 파일로 저장
   - Excel에서 바로 열람 가능

5. **통계 정보 출력**
   - 반별 평균 및 등급 분포
   - 전체 통계
   - 상위 10명 출력

### 실행 방법

```bash
python middle_school_tech_scores.py
```

### 출력 결과

프로그램을 실행하면 다음과 같은 정보가 출력됩니다:

1. **성적 생성 진행 상황**
   - 각 반별 생성 완료 메시지

2. **반별 통계**
   - 기말고사, 수행평가 1, 2, 3 평균
   - 총점 평균
   - 등급 분포 (A, B, C, D, E)

3. **전체 통계 (150명)**
   - 전체 평균 점수
   - 전체 등급 분포 및 비율

4. **상위 10명**
   - 순위, 반, 번호, 이름
   - 각 평가 점수 및 총점, 등급

### 생성되는 파일

**`tech_scores.csv`**
- 전체 150명의 성적 데이터
- 컬럼: 반, 번호, 학생ID, 이름, 기말고사, 수행평가1, 수행평가2, 수행평가3, 총점, 등급
- UTF-8 BOM 인코딩 (Excel에서 한글 깨짐 방지)

### 코드 구조

```python
# 주요 함수
generate_student_name()      # 학생 이름 생성
generate_score()             # 점수 생성 (정규분포)
calculate_grade_by_rank()    # 상대평가 등급 계산
```

---

## 🚀 시작하기

### 필요 사항

- Python 3.6 이상
- 기본 라이브러리만 사용 (별도 설치 불필요)

### 전체 실행

모든 Python 기초 샘플을 순서대로 실행하려면:

```bash
python 01_variables_and_data_types.py
python 02_lists_and_loops.py
python 03_functions_and_modules.py
python 04_dictionaries_and_conditionals.py
python 05_file_handling_and_exceptions.py
```

성적 생성 프로그램 실행:

```bash
python middle_school_tech_scores.py
```

---

## 📖 학습 순서 추천

1. **01_variables_and_data_types.py** - Python 기초 시작
2. **02_lists_and_loops.py** - 자료구조와 반복문
3. **03_functions_and_modules.py** - 함수 작성법
4. **04_dictionaries_and_conditionals.py** - 딕셔너리와 조건문
5. **05_file_handling_and_exceptions.py** - 파일 처리
6. **middle_school_tech_scores.py** - 종합 프로젝트 분석

---

## 💡 학습 팁

- 각 파일의 코드를 직접 실행해보세요
- 주석을 읽으며 코드의 동작을 이해하세요
- 코드를 수정해보며 결과가 어떻게 바뀌는지 확인하세요
- 에러가 발생하면 에러 메시지를 읽고 원인을 파악하세요
- 이해가 안 되는 부분은 Python 공식 문서를 참고하세요

---

## 📝 라이선스

이 샘플 코드는 학습 목적으로 자유롭게 사용할 수 있습니다.

---

## 📧 문의

질문이나 개선 사항이 있으면 언제든지 문의해주세요!

**작성일:** 2026-01-15
