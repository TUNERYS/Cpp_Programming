# 문제 01-3 [매개변수의 디폴트값]
## 문제 1
다음 함수를 '매개변수의 디폴트 값 지정'형태가 아닌, '함수 오버로딩'의 형태로 재구현
```c++
int BoxVolume(int length, int width = 1, int height = 1)
{
    return length * width * height;
}
```
sol) 함수 오버로딩으로 구현한 BoxVolume
```c++
int BoxVolume(int length, int width, int height)
{
    return length * width * height;
}

int BoxVolume(int length, int width)
{
    return length * width * 1;
}

int BoxVolume(int length)
{
    return length * 1 * 1;
}

int BoxVolume(void)
{
    return 1 * 1 * 1;
}
```
<br/>

## 문제2
다음과 같은 함수 오버로딩의 문제점은 무엇인가
```c++
int SimpleFunc(int a = 10)
{
    return a+1;
}

int SimpleFunc(void)
{
    return 10;
}
```
함수에 아무런 인자도 전달되지 않는 경우 두 개의 함수 모두 실행 대상이 되므로 오류 발생