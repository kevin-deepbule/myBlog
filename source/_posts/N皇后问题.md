---
title: N皇后问题
date: 2020-01-02 20:48:01
tags: [C,数据结构]
copyright: true
categories: [数据结构,算法]
related_posts: true
---
## N皇后问题解法
<!--more-->
```cpp
#include<iostream>
#include<cmath>
using namespace std;
int N;
int queue[100];
void Nqueue(int k){
	if(k==N){//作用是判断放的皇后行数是否超过N行 
		for(int i=0;i<N;i++){
			cout <<queue[i]+1<<" ";
		}
		cout<<endl;
		return ;
	}
	for(int i=0;i<N;i++){//遍历k行的各个列 
		int j;
		for(j=0;j<k;j++){//循环判断第k行的第i列，是否可以放置， 
			if(queue[j]==i||abs(queue[j]-i)==abs(k-j)){
				break;
			}
		}
		if(j==k){
			queue[k] = i;
			Nqueue(k+1);
		}
	}	
}
int main(){
		cin>>N;
	Nqueue(0);
	return 0;
}
```
N皇后问题：
递归回溯法求解，实际上是判断每一行上的第i列能否放上这个，不能，则什么都不做，函数返回；i++；如果可以放，赋值，然后调用Nqueue判断是否下一个可以，放，直到K==N，所有的N行全部放完，函数返回也就是回溯，然后判断上一行能不能放到下一个位置；每一行都有自己的i,如果可以向下判断，如果不能，i++,继续判断，如果到i等N还不行，那么函数返回到上一层；上一层继续判断；不考虑；
算法的乐趣，在于弄懂后如此简单，（也不简单），弄不懂犹如天书；
这个递归回溯相当于一个n^n重循环测试；递归回溯够巧妙！