# 문제 01-1 [C++ 기반의 데이터 입출력]
## 문제 1
5개의 정수를 입력 받아서, 그 합을 출력하는 프로그램 작성
```c++
# include <iostream>
using namespace std;

int sum();

int main(void)
{
	int result = 0;
	result = sum();
	cout << "합계 : " << result;
	return 0;
}

int sum()
{
	int num[5];
	int result = 0;
	for (int i = 0; i < 5; i++)
	{
		cout << i +1<< "번째 정수 입력: ";
		cin >> num[i];
		result += num[i];
	}
	return result;
}
```
<br/><br/>

## 문제 2
이름과 전화번호를 문자열의 형태로 입력받아 출력하는 프로그램 작성
```c++
# include <iostream>
using namespace std;

void name();

int main(void)
{
	name();
	return 0;
}

void name() {
	char name[100];
	char phone[100];
	cout << "이름 입력 : ";
	cin >> name;
	cout << "전화번호 입력 : ";
	cin >> phone;
	cout << "이름 : " << name << endl;
	cout << "번호 : "<< phone << endl;
}
```
<br/><br/>

## 문제 3
숫자를 입력받아 해당 숫자의 구구단을 출력하는 프로그램 작성
```c++
# include <iostream>
using namespace std;

void Gugu();

int main()
{
	Gugu();
	return 0;
}

void Gugu() {
	int num;
	cout << "출력할 숫자 : ";
	cin >> num;

	for (int i = 0; i < 9; i++)
	{
		cout << num << 'x' << i + 1 << '=' << num * (i + 1) << endl;
	}
}
```
<br/><br/>

## 문제 4
매달 50만원의 기본급여와 물품 판매가의 12%를 추가 지급받는 판매원의 급여 계산 프로그램 작성
```c++
# include <iostream>
using namespace std;

void Pay();
int Salary(int);

int main(void)
{
	Pay();
	return 0;
}

void Pay() {
	int sell = 0;

	while (1)
	{
		cout << "판매 금액을 만원 단위로 입력 : ";
		cin >> sell;		
		if (sell == -1) { break; }
		
		cout << "이번달 급여 : " << Salary(sell) << "만원" << endl;
	}

	cout << "프로그램 종료" << endl;
}

int Salary(int sell)
{
	return 50 + (sell * 0.12);
}
```