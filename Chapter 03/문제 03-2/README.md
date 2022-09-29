# 문제 03-1 [클래스의 정의]
## 문제 1
4칙연산 기능을 가진 Calculator클래스 구현
어떤 연산을 몇 번 했는지 기록하는 기능도 포함
아래 main함수와 실행의 예에 부합하도록 Calculator클래스를 구현할 것
```C++
int main(void)
{
	Calculator cal;
	cal.Init();
	cout << "3.2 + 2.4 = " << cal.Add(3.2, 2.4) << endl;
	cout << "3.5 / 1.7 = " << cal.Div(3.5, 1.7) << endl;
	cout << "2.2 - 1.5 = " << cal.Min(2.2, 1.5) << endl;
	cout << "4.9 / 1.2 = " << cal.Div(4.9, 1.2) << endl;
	cal.ShowOpCount();
	return 0;
}
```
실행의 예
```
3.2 + 2.4 = 5.6
3.5 / 1.7 = 2.05882
2.2 - 1.5 = 0.7
4.9 / 1.2 = 4.08333
덧셈 : 1 뺄셈 : 1 곱셈 : 0 나눗셈 : 2
```
## 풀이
```C++
class Calculator {
private:
	int numAdd;
	int numMin;
	int numDiv;
	int numMul;

public:
	void Init() {
		numAdd = 0;
		numMin = 0;
		numDiv = 0;
		numMul = 0;
	}

	float Add(float a, float b) {
		numAdd++;
		return a + b;
	}

	float Min(float a, float b) {
		numMin++;
		return a - b;
	}

	float Div(float a, float b) {
		numDiv++;
		return a / b;
	}

	float Mul(float a, float b) {
		numMul++;
		return a * b;
	}
	
	void ShowOpCount() {
		cout << "덧셈 : " << numAdd << ' ' << "뺄셈 : "<< numMin
			<< ' ' << "곱셈 : "<< numMul << ' ' << "나눗셈 : "<< numDiv << endl;
	}
};
```
- 실행 결과
```
3.2 + 2.4 = 5.6
3.5 / 1.7 = 2.05882
2.2 - 1.5 = 0.7
4.9 / 1.2 = 4.08333
덧셈 : 1 뺄셈 : 1 곱셈 : 0 나눗셈 : 2
```