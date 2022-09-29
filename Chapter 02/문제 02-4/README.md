# 문제 02-4 [C++의 표준함수 호출]
## 문제1
아래 c표준함수를 c++에서 호출하는 예제를 만들라(예제 내용 무관)
```c
#include<string.h>
- strlen : 문자열 길이 계산
- strcat : 문자열의 뒤에 덧붙이기
- strcpy : 문자열 복사
- strcmp : 문자열의 비교
```
### 풀이
```c++
#define _CRT_SECURE_NO_WARNINGS
#include <cstdio>
#include <cstring>
using namespace std;

int main(void)
{
	int strlen1 = 0, strlen2 = 0;
	int cmp = 0;

	char* fullstr = new char;

	char str1[] = "This is a result ";
	char str2[] = "of the quest!";
	printf("str1 : %s\n", str1);
	printf("str2 : %s\n", str2);

	strlen1 = strlen(str1);
	strlen2 = strlen(str2);
	printf("str1길이 : %d\n", strlen1);
	printf("str2길이 : %d\n", strlen2);

	cmp = strcmp(str1, str2);
	printf("strcmp결과 : %d\n", cmp);

	strcat(str1, str2);
	printf("strcat결과 : %s\n", str1);

	strcpy(fullstr, str1);
	printf("strcpy결과 : %s\n", fullstr);

	delete[] fullstr;
	return 0;
}
```
결과 확인
```
str1 : This is a result
str2 : of the quest!
str1길이 : 19
str2길이 : 13
strcmp결과 : -1
strcat결과 : This is a result of the quest!
```
<br/>

## 문제 2

