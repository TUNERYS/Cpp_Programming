# 문제 02-1 [참조자 기반의 Call-by-reference 구현]
## 문제 1
참조자를 이용해서 다음의 함수를 각각 정의하여라.   
- 인자로 전달된 int형 변수의 값을 1씩 증가시키는 함수
- 인자로 전달된 int형 변수의 부호를 바꾸는 함수
- 위의 함수를 호출하여 그 결과를 확인하는 main함수
```C++
#include <iostream>
using namespace std;

void Add(int& num); //인자로 전달된 int형 변수의 값을 1씩 증가시키는 함수
void ChangeSymbol(int& num); //인자로 전달된 int형 변수의 부호를 바꾸는 함수

int main(void) //위의 함수를 호출하여 그 결과를 확인하는 main함수
{
	int num4Add = 1;
	int num4Cng = -2;
	
	cout << "before : " << num4Add << ", " << num4Cng << endl;
	
	Add(num4Add);
	ChangeSymbol(num4Cng);


	cout << "after : " << num4Add << ", " << num4Cng << endl;

	return 0;
}

void Add(int& num)
{
	num++;
}

void ChangeSymbol(int& num)
{
	num *= -1;
}
```
- 결과
```
before : 1, -2
after : 2, 2
```
<br/><br/>
## 문제 3
다음 코드에서 ptr1과 ptr2가 가리키는 대상이 서로 바뀌돋록 SwapPointer함수 정의
```C++
int main(void)
{
	int num1 = 5;
	int* ptr1 = &num1;
	int num2 = 10;
	int* ptr2 = &num2;
		:
		:
}
```
- 풀이 및 결과 확인
```C++
#include <iostream>
using namespace std;

void SwapPointer(int* (&ref1), int* (&ref2));

int main(void)
{
	int num1 = 5;
	int* ptr1 = &num1;
	int num2 = 10;
	int* ptr2 = &num2;

	cout << "before : " << * ptr1 << ", " << * ptr2 << endl;

	SwapPointer(ptr1, ptr2);

	cout << "after : " << *ptr1 << ", " << *ptr2 << endl;

	return 0;
}

void SwapPointer(int*(& ref1), int*(& ref2)) {
	int* temp = ref1;
	ref1 = ref2;
	ref2 = temp;
}
```
- 결과
```
before : 5, 10
after : 10, 5
```