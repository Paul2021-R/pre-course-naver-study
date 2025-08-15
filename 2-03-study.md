# 2-03 파이썬 조건문과 반복문, 디버깅 학습 요약

## 학습 목표
사용자 점수를 입력받아 학점을 계산하고 유효성을 검사하는 '성적 계산기' 프로그램을 구현하며, 파이썬의 조건문과 반복문, 그리고 디버깅 개념을 익히는 것이 목표이다.

## 문제 요구사항
*   사용자로부터 점수를 입력받는다.
*   95점 이상 A+, 90점 이상 A, 85점 이상 B+, 80점 이상 B, 70점 이상 C, 60점 이상 D, 60점 미만 F 학점을 부여한다.
*   -1 입력 시 프로그램을 종료한다.
*   0점 미만(단, -1 제외) 또는 100점 초과 시 '유효하지 않은 점수' 메시지를 출력하고 다음 입력을 받는다.
*   유효한 정수 점수만 입력된다고 가정한다.

## 핵심 개념

### 1. 조건문 (Conditionals)
특정 조건에 따라 다른 동작을 수행하는 명령어이다. `if`, `elif`, `else` 키워드를 사용하며, 비교 연산자(<, >, == 등)와 논리 키워드(and, or, not)를 활용한다.

![](/src//2025-08-15-001.png)
< 조건은 다음을 활용하면 된다 

### 2. 반복문 (Loops)
정해진 동작을 반복적으로 수행하는 명령어이다. `for` 루프는 반복 범위를 지정하고, `while` 루프는 조건이 만족하는 동안 반복한다. `break`는 반복문을 즉시 종료하고, `continue`는 현재 반복을 건너뛰고 다음 반복으로 넘어간다.

```python
for looper in [1, 2, 3, 4, 5]:
    print('hello')
for looper in range(0, 5): # 0부터 4까지 
    print('hello')
```

```python
for i in range (1, 10, 2):
    print(i) # 1부터 10까지 2씩 증가시키면서 반복 수행
for i in range (10, 1, -1):
    print(i) # 10부터 1까지 -1씩 증가시키면서 반복 수행
```

### 3. 디버깅 (Debugging)
코드의 오류를 발견하고 수정하는 과정이다. 오류의 '원인'을 알고 '해결책'을 찾아야 한다.

*   **문법적 에러 (Syntax Error)**: 들여쓰기(Indentation Error), 오탈자, 대소문자 구분 오류 등이 있다. 인터프리터가 제공하는 에러 메시지를 분석하여 오류의 원인을 파악할 수 있다.
*   **논리적 에러 (Logical Error)**: 코드의 실행 결과가 예상과 다르게 나오는 경우이다. 중간 `print` 문을 삽입하여 변수 값을 확인하며 코드의 흐름을 추적하여 문제의 원인을 찾아 해결한다.

## 구현 코드

```python
def isAcceptable(numberString):
    try:
        result = int(numberString)
        acceptable = True

        if result < -1 or result > 100:
            acceptable = False
            print('유효하지 않은 점수입니다. 0점에서 100점 사이의 점수를 입력해주세요.')
        return acceptable, result
    except:
        acceptable = False
        return  acceptable, -1

print ('점수를 입력하세요(-1 을 입력하면 종료 됩니다.): ')
while True :
    score_str = input()
    acceptable, score_int = isAcceptable(score_str)

    if score_int == -1 :
        break

    if not acceptable:
        continue

    # conditions
    grade = 'Z'
    if score_int < 60:
        grade = 'F'
    elif score_int < 70:
        grade = 'D'
    elif score_int < 80:
        grade = 'C'
    elif score_int < 85:
        grade = 'B'
    elif score_int < 90:
        grade = 'B+'
    elif score_int < 95:
        grade = 'A'
    else :
        grade = 'A+'

    print (f'당신의 등급은 {grade}({score_int}점) 입니다.')

print ('프로그램을 종료 합니다.')
```

## 결론
이번 학습을 통해 파이썬의 조건문과 반복문을 활용하여 성적 계산기 프로그램을 성공적으로 구현하였다. 특히, 유효성 검사와 오류 처리를 통해 프로그램의 견고성을 높이는 방법을 익혔으며, 디버깅의 중요성을 이해하는 계기가 되었다.
