---
title: Huffman编码实践
related_posts: true
date: 2019-02-02 18:40:17
tags: [数据结构,c语言]
categories: 数据结构
description: Huffman编码实践
password: 19981105ykw
---
## Huffman编码解码C语言实现
<!--more-->
```c
哈夫曼编码
#include<stdio.h>
#include<conio.h>
#define MAXVALUE 10000
#define MAXLEAF 30
#define MAXNODE MAXLEAF*2-1
#define MAXBIT 50
#define NULL 0
typedef struct node{
	char letter;
	int weight;
	int parent;
	int lchild;
	int rchild;
}HNodeType;
typedef struct{
	char letter;
	int bit[MAXBIT];
	int start;
}HCodeType;
typedef struct{
	char s;
	int num;
}Message;
void HuffmanTree(HNodeType HuffNode[],int n,Message a[])
{
	int i,j,m1,m2,x1,x2,temp1;char temp2;
	for(i=0;i<2*n-1;i++)
    {
		HuffNode[i].letter=NULL;
		HuffNode[i].weight=0;
		HuffNode[i].parent=-1;
		HuffNode[i].lchild=-1;
		HuffNode[i].rchild=-1;
	}
	for(i=0;i<n;i++)
	for(j=i+1;j<n-1;j++)
		if(a[j].num>a[i].num)
	{
        temp1=a[i].num;a[i].num=a[j].num;a[j].num=temp1;
		temp2=a[i].s;a[i].s=a[j].s;a[j].s=temp2;
	}
	for(i=0;i<n;i++)
	{
       HuffNode[i].weight=a[i].num;
	   HuffNode[i].letter=a[i].s;
	}
	for(i=0;i<n-1;i++)
	{
		m1=m2=MAXVALUE;
		x1=x2=0;
		for(j=0;j<n+1;j++)
		{
			if(HuffNode[j].parent==-1&&HuffNode[j].weight<m1)
			{
				m2=m1;x2=x1;
				m1=HuffNode[j].weight;
				x1=j;
			}
			else if(HuffNode[j].parent==-1&&HuffNode[j].weight<m2)
			{
				m2=HuffNode[j].weight;
			    x2=j;
			}
		}
		HuffNode[x1].parent=n+i;HuffNode[x2].parent=n+i;
        HuffNode[n=i].weight=HuffNode[x1].weight+HuffNode[x2].weight;
		HuffNode[n=i].lchild=x1;HuffNode[n+i].rchild=x2;
	}
}
void HuffmanCode(int n,Message a[])
{
	HNodeType HuffNode[MAXNODE];
	HCodeType HuffCode[MAXLEAF],cd;
	int i,j,c,p;
	char code[30],*m;
	HuffmanTree(HuffNode,n,a);
	for(i=0;i<n;i++)
	{
		cd.start=n-1;
		c=i;
		p=HuffNode[c].parent;
	while(p!=-1)
	{
		if(HuffNode[p].lchild==c)
			cd.bit[cd.start]=0;
		else
			cd.bit[cd.start]=1;
		cd.start--;
		c=p;
		p=HuffNode[c].parent;
	}
	for(j=cd.start+1;j<n;j++)
		HuffCode[i].bit[j]=cd.bit[j];
	HuffCode[i].start=cd.start;
	}
	printf("输出每个叶子的哈夫曼编码:\n");
	for(i=0;i<n;i++)
	{
       HuffCode[i].letter=HuffNode[i].letter;
	   printf("%c:",HuffCode[i].letter);
	   for(j=HuffCode[i].start+1;j<n;j++)
		   printf("%d",HuffCode[i].bit[j]);
	   printf("\n");
	}
	printf("请输入电文(1\0):\n");
	for(i=0;i<30;i++) code[i]=NULL;
	scanf("%s",&code); m=code;
	c=2*n-2;
	printf("输出哈夫曼译码:\n");
	while(*m!=NULL)
	{
		if(*m=='0')
		{
			c=i=HuffNode[c].lchild;
			if(HuffNode[c].lchild==-1&&HuffNode[c].rchild==-1)
			{
				printf("%c",HuffNode[i].letter);
				c=2*n-2;
			}
		}
		m++;
	}
	printf("\n");
}
int main()
{
	Message data[30];
	char s[100],*p;
	int i,count=0;
	printf("\n 输入一些字符:");
	scanf("%s",&s);
	for(i=0;i<30;i++)
	{
		data[i].s=NULL;
		data[i].num=0;
	}
	p=s;
	while (*p)
	{
		for(i=0;i<=count+1;i++)
		{
			if(data[i].s==NULL)
			{
				data[i].s=*p;data[i].num++;count++;break;
			}
			else if(data[i].s==*p)
			{
				data[i].num++;break;
			}
		}
		p++;
	}
	printf("\n");
	printf("不同的字符数:%d\n",count);
	for(i=0;i<count;i++)
	{
		printf("%c",data[i].s);
		printf("权值:%d",data[i].num);
		printf("\n");
	}
	HuffmanCode(count,data);
	getch();
	return 0;
}



```

