# Chapter02 C언어 기반의 C++2
## 0. 문제풀이 (완성 후 링크 교체 할 것!)
- [문제 02-1](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-1 "question 02-1 link")   
- [문제 02-2](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-2 "question 02-2 link")   
- [문제 02-3](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-3 "question 02-3 link")
- [문제 02-4](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-4 "question 02-3 link")   
<br/>

## 1. [C복습] 키워드 const의 의미
 아래 예시들에서 사용된 (int *)의 괄호는 단지 int * 이 int형 포인터 자료형임을 강조하는 것일 뿐,   
실제로는 괄호를 사용하지 않는다.   
1. 변수 num을 상수화
```C++
const int num = 10;
```   

2. ptr1을 이용해서 val1의 값 변경 불가 (* ptr을 상수화)
```C++
const (int *) ptr1 = &val1;
```   

3. ptr2가 가리키는 대상을 val2의 주소만으로 고정 (ptr을 상수화)
- val2의 값은 변경 가능하다
```C++
(int *) const ptr2 = &val2;
```   

4. 포인터 ptr3가 상수화 
- ptr3값을 이용하여 val3값 변경 불가능 및 ptr3가 가리키는 대상을 val3만의 주소 고정
```C++
const (int *) const ptr3 = &vla3;
```   

## 2. 참조자
1. 참조자란 변수에 또다른 이름을 붙이는 것
2. 참조자의 조건
    - 변수에 대해서만 선언가능, 선언과 동시에 누군가는 참조해야 함
    - 상수를 대상으로 참조자 선언 불가
3. 참조자 기반의 Call-by-reference 함수 호출 진행 가능
```C++
void SwapByValue(int &ref1, int &ref2)
{
    int temp = ref1;
    ref1 = ref2;
    ref2 = temp;
}
```     
4. 함수 내에서 참조자를 이용한 값의 변경을 하지 않는 경우, **const선언**을 추가하는 것이 직관적
```C++
void Func(const int &ref)
```
5. **반환형이 참조형**인 경우 **변수 그 자체를 반환**하는 것
```c++
int & RefRetOne(int & ref)
{
    return ref;
}
```
- 변수 ref 그 자체를 반환
- 변수 그 자체가 반환되므로 참조자가 ref를 받을 수도,
- 다른 일반 자료형의 변수가 ref의 값을 받을 수도 있다.
- 즉, 반환값을 어디에 저장하는 지에 따라 그 결과가 달라짐
- 지역변수는 소멸되기 때문에 참조형으로 반환해서도, 참조자가 받아서도 안된다.
6. **반환형이 일반형**인 경우 **변수에 저장된 값**을 반환
```c++
int RefRetOne(int & ref)
{
    return ref;
}
```
- ref에 저장된 int형 값을 반환
- 저장된 **값**이 반환되므로 참조자가 ref를 받는 것은 불가
- 반드시 변수에 저장해야 함
- 지역변수 반환 가능

7. 상수화된 변수에 대한 참조자 선언은 상수화된 참조자로 선언
```c++
const int num = 10;
const int & ref = num;
```

8. const참조자는 예외적으로 상수도 참조 가능
```c++
int Adder(const int &num1, const int &num2)
{
    return num1 + num2;
}
```
- 단순 상수 인자를 매개변수로 받는 경우 이용
- Adder(2,3)과 같이 호출 가능
- 이때 상수는 **임시변수**로 저장됨

## 3. new & delete
1. C에서의 malloc, free의 단점
    - 할당 대상의 정보를 무조건 **바이트 크기 단위** 전달
    - 반환형이 void포인터이기 때문에 적절한 **형변환** 필수
2. C++에서는 위와 같은 malloc, free의 단점을 제거한 new,delete 사용
3. 사용법은 아래와 같다.
```c++
/***** 할 당 *****/
int * ptr1 = new int;
int * arr1 = new int[3];

/***** 소 멸 *****/
delete ptr1;
delete []arr1;
```
- new 연산 시 , 반환된 주소값을 대상으로 delete연산을 진행
- 할당된 영역이 배열 구조라면 []을 추가하여 배열임을 명시

## 4. C++에서 C언어 표준함수 호출하기
1. C언어의 라이브러리는 C++의 표준 라이브러리에도 포함되어 있음
2. C라이브러리의 헤더 확장자 .h를 생략하고 앞에 c를 붙여주면 됨
3. 사용 예시는 아래와 같다.
```C++
#include <stdio.h>   --->   #include <cstdio>
#include <stdlib.h>  --->   #include <cstdlib>
#include <math.h>    --->   #include <cmath>
#include <string.h>  --->   #include <cstring>  
```

## 5. [C복습] 난수의 생성
