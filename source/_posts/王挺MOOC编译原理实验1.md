---
title: 王挺MOOC编译原理实验1
date: 2020-06-02 20:47:21
tags: 编译原理
copyright: true
categories: 编译原理
related_posts: true
---
王挺MOOC编译原理实验1
<!--more-->
```c
/* begin */
[+]				{printf("%s: PLUS\n",yytext);}
[-]				{printf("%s: MINUS\n",yytext);}
[*]				{printf("%s: TIMES\n",yytext);}
[/]				{printf("%s: DIVSYM\n",yytext);}
[:][=] 			{printf("%s: BECOME\n",yytext);}
['][^']*[']			{printf("%s: CHARCON\n",yytext);}
[\$\!\@\#\%^\&\*\~\_\\]		{printf("%s: ERROR\n",yytext);}
[=]				{printf("%s: EQL\n",yytext);}
[<][>]			{printf("%s: NEQ\n",yytext);}
[<]				{printf("%s: LSS\n",yytext);}
[<][=]			{printf("%s: LEQ\n",yytext);}
[>]				{printf("%s: GTR\n",yytext);}
[>][=]			{printf("%s: GEQ\n",yytext);}
[o][f]			{printf("%s: OFSYM\n",yytext);}
[a][r][r][a][y] {printf("%s: ARRAYSYM\n",yytext);}
[p][r][o][g][r][a][m] {printf("%s: PROGRAMSYM\n",yytext);}
[m][o][d]		{printf("%s: MODSYM\n",yytext);}
[a][n][d]		{printf("%s: ANDSYM\n",yytext);}
[o][r]			{printf("%s: ORSYM\n",yytext);}
[n][o][t]		{printf("%s: NOTSYM\n",yytext);}
[[]				{printf("%s: LBRACK\n",yytext);}
[]]				{printf("%s: RBRACK\n",yytext);}
[(]				{printf("%s: LPAREN\n",yytext);}
[)]				{printf("%s: RPAREN\n",yytext);}
[,]				{printf("%s: COMMA\n",yytext);}
[;]				{printf("%s: SEMICOLON\n",yytext);}
[.]				{printf("%s: PERIOD\n",yytext);}
[:]				{printf("%s: COLON\n",yytext);}
[b][e][g][i][n] {printf("%s: BEGINSYM\n",yytext);}
[e][n][d]		{printf("%s: ENDSYM\n",yytext);}
[i][f]			{printf("%s: IFSYM\n",yytext);}
[t][h][e][n]	{printf("%s: THENSYM\n",yytext);}
[e][l][s][e]	{printf("%s: ELSESYM\n",yytext);}
[w][h][i][l][e] {printf("%s: WHILESYM\n",yytext);}
[d][o]			{printf("%s: DOSYM\n",yytext);}
[c][a][l][l]	{printf("%s: CALLSYM\n",yytext);}
[c][o][n][s][t]	{printf("%s: CONSTSYM\n",yytext);}
[t][y][p][e]	{printf("%s: TYPESYM\n",yytext);}
[v][a][r]		{printf("%s: VARSYM\n",yytext);}
[p][r][o][c][e][d][u][r][e]	{printf("%s: PROCSYM\n",yytext);}
{INTCON}		{printf("%s: INTCON\n", yytext);}
{IDENT}			{printf("%s: IDENT\n", yytext);}

 /* end */
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200417170901228.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0Mzg4NDc2,size_16,color_FFFFFF,t_70)