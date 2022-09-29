# 문제 03-1 [구조체 내에 함수정의하기]
## 문제
2차원 평면상에서의 좌표를 표현하는 구조체를 다음과 같이 정의하였다.
```c++
struct Point {
	int xpos;
	int ypos;
};
```
위 구조체를 기반으로 주어진 main함수가 동작하도록 구조체 내부에 다음 함수를 정의하여라
```c++
void MovePos(int x, int y);
void AddPoint(const Point& pos);
void ShowPosition();
```
주어진 main함수
```c++
int main(void)
{
	Point pos1 = { 12, 4 };
	Point pos2 = { 20, 30 };

	pos1.MovePos(-7, 10);
	pos1.ShowPosition();

	pos1.AddPoint(pos2);
	pos1.ShowPosition();
	return 0;
}
```
함수 실행 예시
```
(5,14)
(25,44)
```

## 풀이
```C++
struct Point {
	int xpos;
	int ypos;

	void MovePos(int x, int y) {
		xpos += x;
		ypos += y;
	}
	void AddPoint(const Point& pos) {
		xpos += pos.xpos;
		ypos += pos.ypos;
	}
	void ShowPosition() {
		cout << '(' << xpos << ',' << ypos << ')' << endl;
	}
};
```
- 실행 결과
```
(5,14)
(25,44)
```