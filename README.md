# merge_sort
```
#include <iostream>
using namespace std;
void merge(int* a, int low, int mid, int hight)  //合并函数
{
	int* b = new int[hight - low + 1];  //b数组辅助运算，存放原A数组的数值
	int i = low, j = mid + 1, k = 0;    
	while (i <= mid && j <= hight)
	{
		if (a[i] <= a[j])
		{
			b[k++] = a[i++];  //按从小到大存放在 b 数组里面
		}
		else
		{
			b[k++] = a[j++];
		}
	}
	while (i <= mid)  // 有一方遍历结束，将另一数组剩余元素依次存放
	{
		b[k++] = a[i++];
	}
	while (j <= hight)
	{
		b[k++] = a[j++];
	}
	k = 0;  
	for (int i = low; i <= hight; i++)  //将 b 数组的值传递给数组 a
	{
		a[i] = b[k++];
	}
	delete[]b;     
}
void mergesort(int* a, int low, int hight) //归并排序
{
	if (low < hight)
	{
		int mid = (low + hight) / 2;
		mergesort(a, low, mid);          //递归地对两数组进行划分
		mergesort(a, mid + 1, hight);    
		merge(a, low, mid, hight);       //进行合并操作
	}
}
int main()
{
	int n, a[100];
	cout << "元素个数为：" << endl;
	cin >> n;
	cout << "请输入各元素：" << endl;
	for (int i = 0; i < n; i++)
	{
		cin >> a[i];
	}
	mergesort(a, 0, n - 1);
	cout << "归并排序结果" << endl;
	for (int i = 0; i < n; i++)
	{
		cout << a[i] << " ";
	}
	cout << endl;
	return 0;
}
```
