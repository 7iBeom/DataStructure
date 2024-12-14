# System Life Cycle
- Software Life Cycle
- Steps of Developments
##### Requirements: 
- 요구사항 분석
- 문제와 결과 정보 규정
##### Analysis:
- 시스템 분석
- Bottom-up Analysis: 
	- 개발 초기에 세부 기능 구현을 강조하기 때문에:
	- 결과 프로그램은 세부 기능의 조합
	- Cons: 문제의 특성을 고려하지 않고 설계가 될 수 있음
- Top-down Analysis:
	- 프로그램을 세그먼트로 분할 (함수 또는 클래스)
	- Cons: **도미노 효과** 발생 가능, 즉 하나의 문제가 전체의 문제가 될 수 있음
##### Design
- 설계
- 설계 접근 관점:
	- 데이터 관점: Abstract Data Type
	- 연산 관점: Algorithm
- 프로그래밍 언어에 독립적
##### Refinement and Coding
- 구현
- 구현 방법 및 알고리즘 선택
- 구현 단계에서는 성능을 고려해야 한다. (Performance)
##### Verification
- 검증
- 정확성 증명:
	- 수학적 기법을 사용하여 정확성을 증명한다 하지만,
	- 시간 소요가 크고 사용 불가능한 경우도 존재함
	- 이를 해결하기 위해, 정확한 알고리즘 사용
	- 구현 전이나 구현 중에 사용 가능
- 검사 (Testing):
	- 실행 코드와 코드를 테스트하기 위한 데이터 필요
	- 모든 가능성을 검사할 수 있는 양질의 테스트 데이터 필요 (타인이 검사)
	- 프로그램 실행 시간 측정
- 오류 제거:
	- 스파게티 코드 주의

>[!note] What makes a good program?
> - Documentation: 코드에 명확한 명시
>	- 주석
>	- 변수명
>	- 함수명
> - Separated code:
>   - 기능적으로 분할
>   - 함수 사용 및 배치

# Algorithm Specification
##### Algorithm Definition
- 작업을 수행하기 위한 유한한 명령어의 나열
##### Conditions of Algorithm
- Input: 0개 이상
- Output: 적어도 하나 이상
- Definiteness: 알고리즘을 구성하는 명령어의 의미는 **명확**해야 한다.
- Finiteness: 알고리즘은 반드시 종료되어야 한다.
- Effectiveness: 모든 명령어는 실행 가능해야 한다.
##### Example of Algorithm
1. Selection Sorting
2. Binary Search

> Algorithm은 구체적인 해결 방안과 구현 방법을 제시해야 하고, Data를 담는 변수의 Type 또한 제시하여야 한다.
> - 매크로와 함수의 이용
> - 매크로: 효율적이지만 소스의 크기가 커진다.
> - 함수: 실행 코드의 크기를 줄여 디버깅에 용이하다. 
# Data Abstraction
## Abstract Data Type (ADT)
##### Definition of ADT
- 데이터 객체 및 연산의 명세와 데이터 객체 내부 표현 양식/연산의 구현 내용을 분리
###### Operation Specification of ADT
- Elements: 함수 이름, 인자의 Type, 결과의 Type
- 함수 호출 방법 및 결과에 대한 설명
- 함수의 내부 동작 과정 및 구현 방법 은폐
###### Internal function types in the operation specification
- Constructor: 객체의 새로운 인스턴스 생성
- Transformer: 기존 인스턴스로 새로운 인스턴스 생성
- Observer: 인스턴스에 대한 정보 출력
###### Example of ADT
- 사용자에게 보이는 서비스인 Function의 기능을 구현하고, 구현 방식은 ADT로 은페한다.
```
ADT Natural_Number
	Object: 0부터 시작하여 컴퓨터로 표현할 수 있는 최대 정수(INT_MAX)까지의 범위에 속하는 정수의 집합
	Function:
		for all x,y in Natural Number; TRUE, FALSE in Boolean and where +, -, < and
		== are the usual integer operations

		Nat_No Zero()       ::= 0
		Boolean Is_Zero()   ::= if (x) return FALSE
								else return TURE
		Nat_No Add(x, y)    ::= if ((x + y) <= INT_MAX) return x + y
								else return INT_MAX
		Boolean Equal(x, y) ::= if (x == y) return TRUE
								else return FALSE
		Nat_No Successor(x) ::= if (x == INT_MAX) return x
								else return x + 1
		Nat_No Sub(x, y)    ::= if (x < y) return 0
								else return x - y
end Natural_Number
```

# Performance Analysis
##### Evaluation Standards
###### Essential Elements
- 주어진 문제 해결
- Correctness
###### Good Programming Habits
- Documentation
- Modularization
- Readability
###### Performance Related
- Space Efficiency
- Time Efficiency
>[!note] Performance Analysis vs. Performance Measurement
>- Performance Analysis: Complexity Theory, Simulation
>	- 환경에 영향을 받지 않는다.
>- Performance Measurement: Benchmarking
>	- 프로그램 실행과 같이 직관적이다.
>	- 환경에 따라 성능이 상이하다.
## Complexity
- Space Complexity: memory
- ==Time Complexity==: executable time

### Time Complexity
- $T_p = compile\ time + executable\ time$
- $T_p$: Program Step
- Program Step: one line of code, count
#### Step Count Table
| Statement                                                                                                                                                                       |       s/e (Step per Execution)       |               Frequency                |               Total Step               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------: | :------------------------------------: | :------------------------------------: |
| Float sum( float list[ ], int n ) <br>{<br>    float tempsum = 0; <br>    int i;  <br>    for ( i = 0; i < n; i++ )<br>        tempsum += list[i]; <br>    return tempsum;<br>} | 0<br>0<br>1<br>0<br>1<br>1<br>1<br>0 | 0<br>0<br>1<br>0<br>n+1<br>n<br>1<br>0 | 0<br>0<br>1<br>0<br>n+1<br>n<br>1<br>0 |
| **Total**                                                                                                                                                                       |                2n + 3                |                   <                    |                   <                    |
- Total Step = s/e * Frequency
- `for()`: Check the condition for ending a loop
### Asymptotic Notation
- $O$ (Big-Oh): Upper bound, $f(n) \leq  cg(n)$
- $\Omega$ (Omega): Lower bound, $f(n) \geq  cg(n)$
- $\Theta$ (Theta): Tight bound (The same of upper bound and lower bound)

#### Time complexity of Algorithm
- Selection Sort: $O(n^2)$
- Binary Search: $O(\log n)$
- Fibonacci Sequence with call the loop: $O(n)$
- Tower of Hanoi with Recursive call: $O(2^n)$
![Pasted image 20240919220347|100](https://github.com/user-attachments/assets/b4e05a85-6836-4890-86b7-694a823102cb)

| Name                        | Notation      |
| --------------------------- | ------------- |
| Constant Time               | $O(1)$        |
| Logarithimc Time            | $O(\log n)$   |
| Linear Time                 | $O(n)$        |
| Quasilinear(loglinear) Time | $O(n \log n)$ |
| Quadratic Time              | $O(n^2)$      |
| Exponential Time            | $O(2^n)$      |
| Factorial Time              | $O(n!)$       |
