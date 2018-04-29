/*计时器判断两个函数的运行时间*/
#include <stdio.h>
#include <stdlib.h>
#include <time.h>                 
#include<math.h>  

#define 循环次数 100000000l;

static double CarmackSqrt(double x);  // Carmack的平方根计算函数

int main(void)
{
	long i = 循环次数;           // 初始化次数
	clock_t 开始, 完成;
	double 耗时;
	/* 测量一个事件持续的时间*/
	printf("做%ld个空循环的时间是: ", i);
	开始 = clock();
	while (i--);
	完成 = clock();
	耗时 = (double)(完成 - 开始) / CLOCKS_PER_SEC;
	printf("%f 秒\n", 耗时);


	/* 对比系统库math.h中的平方根计算sqrt()函数 与Carmack的平方根计算CarmackSqrt()函数 */
	i = 循环次数;            // 初始化次数
	printf("做%ld个CarmackSqrt()循环的时间是: ", i);
	开始 = clock();
	while (i--)
	{
		double x = rand() % 100;
		CarmackSqrt(x);
	}
	完成 = clock();
	耗时 = (double)(完成 - 开始) / CLOCKS_PER_SEC;
	printf("%f 秒\n", 耗时);

	i = 循环次数;            // 初始化次数
	printf("做%ld个sqrt()循环的时间是: ", i);
	开始 = clock();
	while (i--)
	{
		double x = rand() % 100;
		sqrt(x);
	}
	完成 = clock();
	耗时 = (double)(完成 - 开始) / CLOCKS_PER_SEC;
	printf("%f 秒\n", 耗时);
	system("pause");
}

static double CarmackSqrt(double x)
{
	double xhalf = 0.5f * x;

	int i = *(int*)&x;           // get bits for floating VALUE 
	i = 0x5f3759df - (i >> 1);     // gives initial guess y0
	x = *(float*)&i;             // convert bits BACK to float
	x = x*(1.5f - xhalf*x*x);    // Newton step, repeating increases accuracy
	x = x*(1.5f - xhalf*x*x);    // Newton step, repeating increases accuracy
	x = x*(1.5f - xhalf*x*x);    // Newton step, repeating increases accuracy
	return (1 / x);
}
