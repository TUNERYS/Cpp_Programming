# 문제 02-2 [const 포인터와 const 참조자]
## 문제
```c++
const int num = 12;
```
1. 포인터 변수 선언해서 위 변수를 가리키게 하자
2. 이 포인터 변수를 참조하는 참조자를 선언하자
3. 선언된 포인터 변수와 참조자를 이용해서 num에 저장된 값 출력   

- 풀이
```C++
int main(void)
{
	const int num = 12;
	const int* ptr = &num;  //num을 가리키는 포인터 변수 선언
	const int& ref = * ptr; //ptr을 참조하는 참조자

	cout << "num에 저장된 값 : " << num << endl;
	cout << "포인터 변수 ptr이 가리키는 주소에 저장된 값 : " << *ptr << endl;
	cout << "포인터 ptr의 참조자 ref가 가리키는 값 :  " << ref << endl;

	return 0;
}
```
- 결과
```
num에 저장된 값 : 12
포인터 변수 ptr이 가리키는 주소에 저장된 값 : 12
포인터 ptr의 참조자 ref가 가리키는 값 :  12
```

