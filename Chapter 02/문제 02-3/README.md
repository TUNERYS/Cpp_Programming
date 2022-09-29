# 문제 02-3 [구조체에 대한 new & delete 연산]
## 문제
2차원 평면상 좌표를 표현할 수 있는 구조체를 위와같이 정의하였다.
```c++
# include <iostream>
using namespace std;

typedef struct __Point
{
	int xpos;
	int ypos;
} Point;
```
1. 위 구조체를 기반으로 두 점의 함을 계산하는 함수를 아래와 다음의 형태로 정의   
(덧셈결과는 함수의 반환을 통해서 얻을 수 있도록)
```c++
Point& PntAdder(const Point& p1, const Point& p2)
```
2. 임의의 두 점을 선언한 후, 두 점을 이용한 연산을 진행하는 main함수를 정의   
- 이때 구조체 Point관련 변수의 선언은 new연산자를 이용해서 진행하고   
- delete연산자를 통한 소멸도 진행할 것

### 풀이

```c++
# include <iostream>
using namespace std;

typedef struct __Point
{
	int xpos;
	int ypos;
} Point;

Point& PntAdder(const Point& p1, const Point& p2)
{
	Point* res = new Point;  //포인터 변수 res가 point형 크기로 할당된 주소를 가리킴
	res->xpos = p1.xpos + p2.xpos; //res가 가리키는 곳의 xpos
	res->ypos = p1.ypos + p2.ypos; //res가 가리키는 곳의 ypos
	
	return * res;
	// 지역변수 res를 반환하는 것이 아닌 res가 가리키는 값을 반환하는 것
	// 다시말해 메모리에 할당된 Point를 가리키는 res를 통해 Point에 저장된 값이 반환
	// 따라서 지역변수를 참조형으로 반환하면 안되는 문제와 위 함수는 관계가 없다..
}
int main(void)
{
	Point * pnt1 = new Point;
	pnt1 -> xpos = 1;
	pnt1 -> ypos = 2;

	Point * pnt2 = new Point;
	pnt2->xpos = 3;
	pnt2->ypos = 4;

	Point & res = PntAdder(*pnt1, *pnt2); //메모리에 할당된 이름없는 Point구조체를 참조하게 됨.
	cout << "pnt1 : " << pnt1->xpos << ", " << pnt1->ypos << endl;
	cout << "pnt2 : " << pnt2->xpos << ", " << pnt2->ypos << endl;
	cout << "두 점의 합 : " << res.xpos << ", " << res.ypos << endl;

	delete pnt1; //pnt1, pnt2는 힙 영역에 할당된 주소값을 저장하고 있다.
	delete pnt2;
	delete &res; //res자체는 구조체에 저장된 값을 의미 / res가 가리키는 힙 영역을 지워줘야 하기 때문에 &연산자를 사용
	return 0;
}
```
결과 확인
```
pnt1 : 1, 2
pnt2 : 3, 4
두 점의 합 : 4, 6
```

