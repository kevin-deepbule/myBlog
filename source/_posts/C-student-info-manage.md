---
title: 基于C语言的学生成绩管理系统
related_posts: true
date: 2019-02-02 18:56:01
tags: C
description: ''
categories: C
---
## 基于C语言的学生信息管理系统
<!--more-->
## 一、系统需求与功能分析
1.1 系统需求分析   
(1) 能完成学生信息的录入，插入、修改、删除、输出、查询等功能；
(2)采用单链表存储结构实现；
(3) 所有数据以外部文件方式保存。
1.2系统功能分析
(1)要设计一个学生信息管理系统，其功能包括：
①录入函数Add()：将学生信息按尾插法插入到链表中；
②插入函数Insert()：根据所给学号作为插入位置，在其后插入信息；
③修改函数Modify()：修改指定的学生信息；
④删除函数Delete()：当需要删除的学号和姓名一致时则删除对应的学生记录；
⑤输出函数Show()：显示全部学生信息；
⑥查询函数Search()：分别可以按学号和按姓名进行学生信息查询；
⑦菜单函数Menu()：为程序的菜单函数为实现各种功能提供便捷；
⑧读取数据函数Read()：从外部文件读取学生信息信息；
⑨保存数据函数Save()：将数据保存到外部文件中。
(2)线性表的链接存储结构称为单链表，单链表使用一组任意的存储单元存放线性表的元素，这组存储单元可以连续也可以不连续，甚至可以零散分布在内存中的任意位置。为了正确表示元素之间逻辑关系，每个存储单元在存储数据元素的同时，还必须存储其后继元素所在地址信息，这个地址信息称为指针，这两部分组成了数据元素的存储映像，称为结点，结点结构如图1.1所示。
 
图1.1单链表的结点构造
 设p是一个指针变量，则p的值是一个指针。设指针p指向某个结点，则该结点用*p表示，在单链表中，结点p由两个域组成：存放数据元素的部分和存放后继结点地址的指针部分，分别用p->data和p->next来标识，p->next指向结点ai+1，其指针与结点之间关系如图1.2所示。
 
图1.2指针与结点之间关系的示意图
1.3系统性能分析
1．硬件环境
处理器：CPU主频在500MHz以上 
内存：128MB以上
硬盘空间：10MB。
2．软件环境
操作系统: Windows 98/Me/NT/2000/XP(推荐使用Windows 2000/XP)。
调试环境: Visual C++及以上版本。

 

## 二、总体结构设计
2.1系统的结构设计
通过对学生信息管理系统的功能分析，可以定义出系统的总体结构模块图，如图2.1所示。
 
图2.1学生信息管理系统总体结构设计
2.2系统管理流程图
  前面的分析中已经定义了系统各个模块，属于静态建模的范围。在系统运行时刻的动态模型应该由系统的流程决定。当用户运行该系统后可以来进行学生信息信息（录入）插入管理、学生信息修改管理、学生信息删除管理、学生信息显示管理及学生信息显示等操作，具体的流程如图2.2所示。
 
图2.2系统流程图
主模块应负责应用程序的主界面，由它调用其他模块.因此主模块应具有操作性好、界面清晰的特点，使用户能够很方便地找到所需功能。
根据功能需求的结果分析，主界面应该由学生信息录入管理，学生信息插入管理，学生信息修改管理、学生信息删除管理、学生信息显示管理和学生信息信息查询管理组成，可以通过输入相应的数字进入相应的功能模块。

 

三、 系统详细设计和系统实现
系统总体设计完成后，就可以根据需求对各个模块来进行实现了。在本系统中需要编码实现的主要有学生信息信息插入、学生信息信息查询、学生信息信息修改、学生信息信息删除和学生信息信息输出等5个模块。
(1)学生信息录入模块
添加的信息包括姓名(允许重复)、学号(不允许重复)、年龄、性别、宿舍地址、计算机成绩、数学成绩和英语成绩。流程图如下图3.1所示。
 
图3.1录入模块流程图
本程序采用的是尾插法，就是每次将新申请的结点插在终端结点的后面，其执行过程如图3.12所示。
 
图3.12尾插法建立单链表操作示意图
(2)学生信息插入模块
输入一个存在的学号作为插入位置，在其后插入的信息包括姓名、学号、年龄、性别、宿舍地址、计算机成绩、数学成绩和英语成绩。流程图如下图3.2所示。
 
图3.2插入模块流程图
本程序采用的是尾插法，就是每次将新申请的结点插在终端结点的后面，其执行过程如图3.22所示。

 
图3.22 尾插法插入操作示意图

(3)学生信息修改模块
首先要查找与要修改数据相匹配的信息，若没有则返回失败。否则把相应的信息输出，然后再重新输入新的数据并保存到单链表。

(4)学生信息删除模块
当选择删除功能时，首先输入要删除的同学的姓名，然后输入要删除的同学的学号，如果该同学存在并且姓名与学号匹配的上，则进行删除操作，否则返回失败。其流程图3.4如下：
 
图3.4删除学生信息模块流程图
删除操作定义为将单链表的第i个结点删去。因为在单链表中结点ai存储地址在其前驱结点ai-1的指针域，所以必须首先找到ai-1的存储地址p，然后令p的next域指向ai 的后继结点，即把结点ai 从链上摘下来，最后释放结点ai的存储空间，如图3.42所示。 
 
图3.42在单链表中删除结点指针的变化情况

(5)学生信息显示模块
从单链表表头遍历整个单链表，将所有数据输出。其部分代码如下：

     void Function::Show()        
    {	
    	Student *temp;
    	system("cls");
    	temp=Student_First->Next;         
    	if(!temp)                  
    	{	cout<<"文件无数据\n\n "<<endl;
    		cout<<"按任意键返回主菜单"<<endl;
    	    getch();
    		 
        	Menu();           
    	}
    	else
    	{cout<<"姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
    		while(temp!=NULL)
    		{	 temp->Out();
    	        temp=temp->Next;     				
    		}
    	}
    	cout<<endl<<"按任意键返回主菜单"<<endl;
    	getch();
    	
    	Menu();                      
    } 

(6)学生信息查询模块
按姓名和学号查找学生信息的流程图分别如下图3.6所示。

 
图3.6按姓名或学号查找学生信息信息流程图
在单链表中，即使知道被访问结点的位置i，也不能像顺序表那样直接按序号访问，而只能从头指针出发，设置一个工作指针p，顺next域逐个结点往下搜索。当p指向某个结点时判断是否为第i个结点，若是则查找成功；否则，将工作指针p后移，即将p指向原来所指结点的后继结点。直到p为NULL时查找失败。单链表查找过程如图3.62所示。
 
图3.62单链表查找过程的示意图


 
四、 系统测试
在完成了系统各方面的设计后，并不是可以运行就完成的，为了保证系统性能的稳定性跟安全性等，就要对系统做测试。
测试环境如下：
	硬件:联想ThinkPad 2.4GHz，500GB硬盘，4G内存；
	软件:Windows 7 Personal SP1，分辨率1366*768，Microsoft Visual C++ 6.0。

在对系统功能进行逐一测试的时候，遇到了一些问题，例如，因为把学号定义为整形（int），在输入以0为开头的学号时，系统会自动把0去掉，这样学号的信息就丢失了第一位。为了解决这个问题，将学号改成了 字符型(char)，这样在构造函数里也需要把学号的初始化用 字符串拷贝（strcpy）来实现。
遇到的问题还有很多，例如数据出错，内存溢出等，经过反复测试，调试和努力修正，程序得以完善。
下面为源码：

 

    // 程序名称：Student.cpp 
    // 程序功能：采用链表与文件实现一个简单的学生成绩管理系统。
    
    #include <iostream>
    #include <fstream>
    #include<cstring>
    #include<conio.h>
    #include<windows.h>
    #include <ctime>
    using namespace std;
    struct Class
    {   int Computer;
        int Math;
        int English;
    };
    class Student{
    public:
        Student();
        void Ofile(ofstream &of);                 
    	void Infile(ifstream &f);                
        void Out();                                                 
    	void Set(char *name,char *no,int age,char *sex,char *add,Class score);
        char *GetName();                        
    	char * GetNo();                         
    	Student *Next;                           
    protected:
    	char Name[20];                          
        char No[20];	
    	int Age;
    	char Sex[20];
    	char Add[40];
    	Class Score ;
    };
    Student::Student():Next(0){}                   
    char *Student::GetName(){return Name;}        
    char *Student::GetNo(){return No;}
    void Student::Set(char *name,char *no,int age,char *sex,char *add,Class score)
    {	strcpy(Name,name);
    	strcpy(No,no);
    	Age=age;
    	strcpy(Sex,sex);
    	strcpy(Add,add);
        Score=score;
    }
    void Student::Infile(ifstream &f)
    {	f>>Name>>No>>Age>>Sex>>Add>>Score.Computer>>Score.Math>>Score.English;    //将数据输入到文件                
    }
    void Student::Ofile(ofstream &of)
    {	of<<" "<<Name<<" "<<No<<" "<<Age<<" "<<Sex<<" "<<Add<<" "<<Score.Computer<<" "<<Score.Math<<" "<<Score.English;          //从文件中提取数据
    }
    void Student::Out()
    { 
    	cout<<"-------------------------------------------------------------------------------"<<endl;
    	cout<<Name<<"\t"<<No<<"\t"<<Age<<"\t"<<Sex<<"\t"<<Add<<"\t  "<<Score.Computer<<"\t   "<<Score.Math<<"\t  "<<Score.English<<endl; 
    }
    class Function                             //功能类                   
    {
    public:
    	Function();                            //构造函数
    	~Function();                          //析构函数
    	void Menu();                          //菜单函数
    	void Add();                           //录入学生信息函数
    	void Insert();						  //插入学生信息函数
        void Modify();						  //修改学生信息函数
    	void Delete();                         //删除学生信息函数                         
    	void Show();                           //显示学生信息函数
    	void Search();                        //查询学生信息函数
    	
    private:
    	Student *Student_First;                         
    	void Read();                           //读取学生信息函数
        void Save();                           //保存学生信息函数
    };
    Function::Function()
    {    Student_First=new Student;                             
        Read();
    }  
    Function::~Function()
    {	delete Student_First;            
    }
    void Function::Add()                           //录入学生信息函数
    {	char name[20];
        char no[20]; 
    	int age;
    	char sex[20];
    	char add[100];
    	Class score;
    	char choose;                            
    	Student *f1,*p,*f2;                         
    	system("cls");
    	f1=Student_First;
    	f2=Student_First->Next;
    	while(f1->Next)
    		f1=f1->Next;                  
    	do
    	{  p=new Student;
    		cout<<"请输入您要添加的学生成绩信息:"<<endl;
    		cout<<"请输入学生姓名: ";
        	cin>>name;
    		cout<<"请输入学号: ";
        	cin>>no;
    		while(f2)
    		{	if(strcmp(f2->GetNo(),no)==0)
    			{	cout<<"该学生已存在，请确定学号!\n\n";
    			cout<<"1.返回主菜单\n2.继续添加 ------- ";
    			cin>>choose;
    			while(choose!='1'&&choose!='2')
    			{		cout<<"1.返回主菜单\n2.继续添加 ------- ";
    					 cin>>choose;
    			}
    			if(choose=='1')
    			Menu();
    			else if(choose=='2')
    
    				Add();
    			}
    			f2=f2->Next;
    		}
        	
    		cout<<"请输入年龄: ";
    		cin>>age;
    		cout<<"请输入性别: ";
    		cin>>sex;
    		cout<<"请输入宿舍地址: ";
    		cin>>add;
    
        	cout<<"请输入计算机成绩: ";
           cin>>score.Computer;
        	cout<<"请输入数学成绩: ";
           cin>>score.Math;
        	cout<<"请输入英语成绩: ";
        	cin>>score.English;
        	p->Set(name,no,age,sex,add,score);
    		f1->Next=p;                  
    		p->Next=NULL;
    		f1=f1->Next;
    		cout<<"是否继续输入信息?(Y\\N) ------- ";
    		cin>>choose;
    		}while(choose=='y'||choose=='Y');
    	Save();
    	Menu();
    }
    
    void Function::Insert()  
    {
    	char name[20];
        char no[20]; 
    	int age;
    	char sex[20];
    	char add[100];
    	Class score;
    	int flag(0);
    	Student *f1,*p;                         
    	system("cls");
    	f1=Student_First;
    	                    
    	
    	 p=new Student;
    		cout<<"请输入学号来确定插入位置:"<<endl;
    		cin>>no;
    		while(f1)
    			{	if(strcmp(f1->GetNo(),no)==0)        
    				{	flag=1;		    		
    					break;
    				}
    				f1=f1->Next;         
    			}
    				if(flag==0)
    			{
    				cout<<"\n无该学生的信息,程序将返回主菜单\n"<<endl;
    				Sleep(2000);
    				Menu();
    			}
    
    			else
    			{	
    			cout<<"请输入学生姓名: ";
        		cin>>name;
        		cout<<"请输入学号: ";
        		cin>>no;
    			cout<<"请输入年龄: ";
    			cin>>age;
    			cout<<"请输入性别: ";
    			cin>>sex;
    			cout<<"请输入宿舍地址: ";
    			cin>>add;
    
        		cout<<"请输入计算机成绩: ";
    			 cin>>score.Computer;
        		cout<<"请输入数学成绩: ";
    			 cin>>score.Math;
        		cout<<"请输入英语成绩: ";
        		cin>>score.English;
        		p->Set(name,no,age,sex,add,score);
    			}
    		                  
    		p->Next=f1->Next;
    		f1->Next=p;
    		Save();
    		cout<<"插入成功! ";
    		Sleep(1500);
    	
    	Menu();
    }
    
    void Function::Modify()                 //修改学生信息函数
    {	
    	int flag(0);
    	char choose,name[20];               
    	Student *temp,*p;                           
        char no[20];
    	int age;
    	char sex[20];
    	char add[100];
    	Class score;
    	system("cls");
    	temp=p=Student_First;
    	cout<<"输入修改方式：\n1.按姓名修改\n2.按学号修改 ------- ";
    		cin>>choose;
    		if(choose=='1')
    		{	
    			cout<<"请输入您要修改的姓名:\n  ";
    			cin>>name;
    	while(temp)
    	{	if(strcmp(temp->GetName(),name)==0)          
    		{
    			flag=1;
    			cout<<"\n姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
    			temp->Out();
    		    cout<<"请输入姓名: ";
             	cin>>name;                                   
        	    cout<<"请输入学号: ";
            	cin>>no;
    			cout<<"请输入年龄: ";
    			cin>>age;
    			cout<<"请输入性别: ";
    			cin>>sex;
    			cout<<"请输入宿舍地址: ";
    			cin>>add;
            	cout<<"请输入计算机成绩: ";
            	cin>>score.Computer;                                       
            	cout<<"请输入数学成绩: ";
    			 cin>>score.Math;
            	cout<<"请输入英语成绩: ";
    			cin>>score.English;
    			temp->Set(name,no,age,sex,add,score);
    			
    			break;
    		}
    		temp=temp->Next;  
    			
    	}
    	}
    		else if(choose=='2')
    		{	
    			cout<<"请输入您要修改的学号: ";
    			cin>>no;
    			while(temp)
    			{	if(strcmp(temp->GetNo(),no)==0)        
    				{	
    					flag=1;
    					cout<<"\n姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
    					temp->Out();
    					cout<<endl;
    					cout<<"请输入姓名: ";
             			cin>>name;                                   
        				cout<<"请输入学号: ";
            			cin>>no;
    					cout<<"请输入年龄: ";
    					cin>>age;
    					cout<<"请输入性别: ";
    					cin>>sex;
    					cout<<"请输入宿舍地址: ";
    					cin>>add;
            			cout<<"请输入计算机成绩: ";
            			cin>>score.Computer;                                       
            			cout<<"请输入数学成绩: ";
    					 cin>>score.Math;
            			cout<<"请输入英语成绩: ";
    					cin>>score.English;
    					temp->Set(name,no,age,sex,add,score);
    			
    					break;
    				}
    				temp=temp->Next;        
    			
    		}		
    	}
    if(flag==0)
    	cout<<"\n无该学生的信息\n"<<endl;
    else
    {
    	Save();
    	cout<<"修改成功!"<<endl;
    }
    
    	cout<<"1.返回主菜单\n2.继续修改 ------- ";
    	cin>>choose;
    	while(choose!='1'&&choose!='2')
    	{	 cout<<"1.返回主菜单\n2.继续修改 ------- ";
    	    cin>>choose;
    	}
    	if(choose=='1')
    		Menu();
    	else if(choose=='2')
    		Modify();
    }
    
    void Function::Delete()           //删除学生信息函数
    { 	char name[20];               
    	char no[20];
    	char choose;
    	Student *temp,*p;
    	system("cls");
    	p=temp=Student_First->Next;
        cout<<"请输入姓名: ";
    	cin>>name;
    	cout<<"输入学号: ";
    	cin>>no;
    	while(temp)
    	{ if(strcmp(temp->GetName(),name)==0&&strcmp(temp->GetNo(),no)==0)  //判断该学生信息是否存在
    		{      cout<<"姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
           		temp->Out();
           		cout<<"\n是否删除(Y/N) -------";
                  cin>>choose;
    	        if(choose=='y'||choose=='Y')
    			{	p->Next=p->Next->Next;
    				delete temp;
    				cout<<"删除成功:\n";
    			}
    		   	break;                    
    		}
    		p=temp;
    	    temp=temp->Next; 
    	}
        Save();                                     
    	cout<<"1.返回主菜单\n2.继续删除 ------- ";
    	cin>>choose;                              
    	while(choose!='1'&&choose!='2')
    	{	cout<<"1.返回主菜单\n2.继续删除 ------- ";
    	    cin>>choose;
    	}
    	if(choose=='1')
    		Menu();                               
    	else if(choose=='2')
    		Delete();                    
    }
    
    void Function::Read()                       //读取学生信息函数
    {	Student *p,*p2;
        p=Student_First;                            
        ifstream is("Student.txt",ios::in);         
        if(!is)                             
    	{   ofstream os("Student.txt",ios::out);     
            os.close();                        
            return ;
    	}
        while(!is.eof())
    	{   p2=new Student;                   
            p2->Infile(is);
            p->Next=p2;                      
            p2->Next=NULL;                  
             p=p->Next;
    	}
    }
    void Function::Save()                                 //保存学生信息函数
    {	ofstream of("Student.txt",ios::out);         
    	Student *p=Student_First->Next;                      
    	while(p)
    	{	p->Ofile(of);                       
    		p=p->Next;                      
    	}
    	of.close();
    }
    void Function::Search()                       
    {	int flag(0);                           
    	char choose;                          
    	char t1[20];
    	char t2[20];
    	system("cls");
    	Student *temp=Student_First->Next;            
        do
    	{   cout<<"输入查询方式：\n1.按姓名查询\n2.按学号查询 ------- ";
    		cin>>choose;
    		if(choose=='1')
    		{	cout<<"请输入您要查询的姓名:";
    			cin>>t1;	
    			while(temp)
    			{	if(strcmp(t1,temp->GetName())==0)        
    				{	flag=1;	
    					break;
    				}
    				temp=temp->Next;         
    			}
    			if(flag==0)
    				cout<<"\n无该学生的信息\n"<<endl;
    			else
    			{	
    				cout<<"\n";
    				cout<<"姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
    				temp->Out();
    			}
    			break;
    		}
    		else if(choose=='2')
    		{	cout<<"请输入您要查询的学号 ------- ";
    			cin>>t2;
    			while(temp)
    			{	if(strcmp(t2,temp->GetNo())==0)        
    				{	flag=1;		    		
    					break;
    				}
    				temp=temp->Next;         
    			}
    			if(flag==0)
    				cout<<"\n无该学生的信息\n"<<endl;
    			else
    			{	
    				cout<<"\n";
    				cout<<"姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
    				temp->Out();
    			 }
    			break;
    		}
    	}while(choose!='1'||choose!='2');
        cout<<"\n1.返回主菜单\n2.继续查询 ------- ";
    	cin>>choose;
    	while(choose!='1'&&choose!='2')
    	{	cout<<"1.返回主菜单\n2.继续查询 ------- ";
    		cin>>choose;
    	}
    	if(choose=='1')
    		Menu();               
    	else if(choose=='2')
         	Search();           	
    }
    void Function::Show()        
    {	
    	Student *temp;
    	system("cls");
    	temp=Student_First->Next;         
    	if(!temp)                  
    	{	cout<<"文件无数据\n\n "<<endl;
    		cout<<"按任意键返回主菜单"<<endl;
    	    getch();
    		 
        	Menu();           
    	}
    	else
    	{	cout<<"姓名\t学号\t\t年龄\t性别\t宿舍住址\t  计算机   数学   英语\n";
    		while(temp!=NULL)
    		{	 temp->Out();
    	        temp=temp->Next;     				
    		}
    	}
    	cout<<endl<<"按任意键返回主菜单"<<endl;
    	getch();
    	
    	Menu();                      
    }
    void Function::Menu()
    {   system("color F9");
    	time_t t;
        time(&t);
    	char choose;               
    	system("cls");	
    
        cout<<endl;
        cout<<"\t※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※"<<endl;
        cout<<"\t                        西安科技大学欢迎您                 "<<endl<<endl; 
        cout<<"\t		          学生信息管理系统                    "<<endl<<endl; 
        cout<<"\t     当前系统时间: "<<ctime(&t)<<""<<endl;
    	cout<<"\t                                            版权所有：李晋旭 杨凯文"<<endl; 
        cout<<"\t※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※※"<<endl<<endl;
    	cout<<"请按键选择需要的操作 （请输入数字）"<<endl;
        cout<<"\n";
    
    	cout<<"  ╭--------------------------------------╮"<<endl;
      	cout<<" │          1 录入学生信息:               │"<<endl;
    	cout<<" │          2 插入学生信息:               │"<<endl;
        cout<<" │          3 修改学生信息:               │"<<endl;
    	cout<<" │          4 删除学生信息:               │"<<endl;
    	cout<<" │          5 显示全部学生信息:           │"<<endl;
        cout<<" │          6 查找学生信息:               │"<<endl;
    	cout<<" │          7 退出系统:                   │"<<endl;
    	cout<<" ╰----------------------------------------╯"<<endl;
    	cout<<"\n";
        cin>>choose;
    	switch(choose)
    {	case '1': Add();break;                 
    	case '2': Insert();break;
        case '3': Modify();break;
    	case '4': Delete();break;
    	case '5': Show();break;
        case '6': Search();break;
    	case '7': exit(1);break;	
    	default:
    		{	cout<<"请按规定输入选择项!"<<endl;
    			Sleep(1500);
    			Menu();
    		}
    	}
    }
    int main()
    {	Function function;          //定义功能接口
    	function.Menu();            //调用主菜单
    }                                       

