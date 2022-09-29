# Chapter03 클래스의 기본
## 0. 문제풀이 (완성 후 링크 교체 할 것!)
- [문제 02-1](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-1 "question 02-1 link")   
- [문제 02-2](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-2 "question 02-2 link")   
- [문제 02-3](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-3 "question 02-3 link")
- [문제 02-4](https://github.com/TUNERYS/Cpp_Programming/tree/main/Chapter%2002/%EB%AC%B8%EC%A0%9C%2002-4 "question 02-3 link")   
<br/>

## 1. C++에서의 구조체
1. 구조체 등장 배경 : 연관있는 데이터를 하나로 묶으면, 프로그램의 구현 및 관리가 용이
2. 구조체 변수 선언
    - C에서의 구조체 변수 선언
    ```C
    struct Car basicCar; // Car형 구조체 변수 basicCar 선언
    ```
    - C++에서의 구조체 변수 선언
    ```C++
    Car basicCar; // Car형 구조체 변수 basicCar 선언
    ```
    - 위와 같이 C++에서는 struct가 생략된다.
3. 구조체에 종속적인 함수
    - 구조체에 관련된 데이터의 처리를 담당하는 함수를 구조체에 종속적인 함수라 함
    - C에서와는 다르게 C++에서는 구조체 내부에 함수가 포함 될 수 있다. 
    - 구조체 내에 정의된 함수의 수가 많거나 길이가 긴 경우 구조체 밖으로 함수의 정의를 뺄 수도 있다.
    ```C++
    struct Car{
        void ShowCarState();
        void Accel();
    };

    void Car::ShowCarState(){
        .......
    }

    void Car::Accel(){
        .......
    }
    ```
4. 구조체 안에 함수가 정의되어 있는 경우 함수를 인라인으로 처리하게 된다.
5. 함수의 정의를 구조체 밖으로 빼면 인라인으로 처리하지 않는다.
6. 인라인의 의미를 그대로 유지하고 싶은 경우 아래와 같이 인라인 처리를 명시적으로 지시해야 한다.
    ```C++
    inline void Car::ShowCarState(){.......}
    inline void Car::Accel(){.......}
    ```    
<br/><br/>
## 2. 열거형 enum의 사용 (C복습 및 C++에서의 응용)
1. 연관있는 이름을 동시에 상수로 선언하기 위해 사용
2. 선언 방법은 아래와 같다
```c++
enum { Do=1, Re=2, Mi=3, Fa=4, So=5, La=6, Si=7};
```
3. 열거형이 특정 구조체에만 연관 았는 경우, 구조체 내에서 유효한 상수를 정의할 수 있다.   
4. 구조체 내부에 삽입하는 것이 부담스러운 경우, 이름공간을 이용해 상수가 사용되는 영역을 명시할 수도 있다.