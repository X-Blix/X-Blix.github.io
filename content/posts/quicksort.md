---
title: "Quicksort"
date: 2023-08-16T15:31:33+08:00
draft: false
description: 这是一个C++写的快速排序
tags: [C++, 快速排序]
comment : false
---


## 排序

排序（sorting）就是整理数据的顺序，使其从无序变为有序的过程


## 快速排序

1、快读排序其实并不难。我们先确定一个数字，把它作为基准

2、通过一系列的交换比较，让基准达到一个合适的位置

3、保证基准前面得数字都比它小，后面的数字都比它大。

![quicksort](/img/quicksort.png)

## 排序过程

要实现这个过程呢，需要我们使用两个指针，也就是数组的下标 X指向数组的第一个数字，Y指向数组的一个数字。为了操作方便，我们一般以第一个数字为基准值。然后从Y开始移动

![quicksort1](/img/quicksort1.png)

## 代码实现
接下来，就是我们要对3的前面和3的后面做同样的操做，也就是递归。

只知道原理是仅仅不够的，把代码写出来才是真正的王道

```go
#include <iostream>
using namespace std;

void quicksort(int arr[],int left,int right)
{
	if(left>right)
	{
		return ;
	}
	int i = left;
	int j = right;
	int key =  arr[left];
	while(i!=j)
	{
		while((i<j)&&(arr[j]>=key))
		{
			j--;
		}
		while((i<j)&&(arr[i]<=key))
		{
			i++;
		} 
		
		swap(arr[i],arr[j]);
		
	}
	swap(arr[left],arr[i]);
	
	quicksort(arr,left,i-1);
	quicksort(arr,i+1,right);
	
}


int main()
{
	int a[] = {1,3,5,6,2,4};
	quicksort(a,0,5);
	for(int i =0;i<=5;i++)
	{
		cout<<a[i]<<endl;
	}
	return 0;
}




```

### 复习记录
* 2023.8.16  
1. 首先从后向前移动j指针，其次从前往后移动i指针。
2. key值是指向数组里的第一位中的内容，所以key = arr[left] 
3. 交换的时候是arr[left]与arr[i]进行交换。 
