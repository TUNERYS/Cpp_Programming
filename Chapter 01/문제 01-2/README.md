# 문제 01-2 [함수 오버로딩]
## 문제 1
다음 메인 함수에서 필요로 하는 swap합수를 오버로딩해서 구현해보자
```c++
int main(void)
{
	int num1 = 20, num2 = 30;
	swap(&num1, &num2);

	char ch1 = 'A', ch2 = 'Z';
	swap(&ch1, &ch2);

	double dbl1 = 1.111, dbl2 = 5.555;
	swap(&dbl1, dbl2);

	return 0; 
}
```
<br/>
오버로딩으로 구현한 swap함수

```c++
void swap(int* ptr1, int* ptr2)
{
	int temp = *ptr2;
	*ptr2 = *ptr1;
	*ptr1 = temp;
}

void swap(char* ptr1, char* ptr2)
{
	char temp = *ptr2;
	*ptr2 = *ptr1;
	*ptr1 = temp;
}

void swap(double* ptr1, double* ptr2)
{
	double temp = *ptr2;
	*ptr2 = *ptr1;
	*ptr1 = temp;
}
```