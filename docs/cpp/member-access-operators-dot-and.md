---
title: "成员访问运算符：. 和 -&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "."
  - "->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ". 运算符"
  - "-> 运算符"
  - "点运算符 (.)"
  - "成员访问"
  - "成员访问, 表达式"
  - "成员访问, 运算符"
  - "运算符 [C++], 成员访问"
  - "后缀运算符"
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 成员访问运算符：. 和 -&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
      postfix-expression   
      . name  
postfix-expression –> name  
```  
  
## 备注  
 成员访问运算符 **.** 和 **\-\>** 用来引用结构、联合和类的成员。  成员访问表达式具有选定成员的值和类型。  
  
 有两种形式的成员访问表达式：  
  
1.  在第一种形式中，*postfix\-expression* 表示结构、类或联合类型的值，*name* 为指定的结构、联合或类的成员命名。  运算的值是 *name* 的值且为左值（如果 *postfix\-expression* 是左值）。  
  
2.  在第二种形式中，*postfix\-expression* 表示指向结构、联合或类的指针，*name* 为指定的结构、联合或类的成员命名。  该值是 *name* 的值且是左值。  **–\>** 运算符取消引用该指针。  因此，表达式 *e***–\>**`member` 和 **\(\****e***\)**.`member`（其中，*e* 表示指针）会产生相同的结果（重载运算符 **–\>** 或 **\*** 的情况除外）。  
  
## 示例  
 以下示例演示成员访问运算符的两种形式。  
  
```  
// expre_Selection_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Date {  
   Date(int i, int j, int k) : day(i), month(j), year(k){}  
   int month;  
   int day;  
   int year;  
};  
  
int main() {  
   Date mydate(1,1,1900);  
   mydate.month = 2;     
   cout  << mydate.month << "/" << mydate.day  
         << "/" << mydate.year << endl;  
  
   Date *mydate2 = new Date(1,1,2000);  
   mydate2->month = 2;  
   cout  << mydate2->month << "/" << mydate2->day  
         << "/" << mydate2->year << endl;  
   delete mydate2;  
}  
```  
  
  **2\/1\/1900**  
**2\/1\/2000**   
## 请参阅  
 [后缀表达式](../cpp/postfix-expressions.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [类和结构](../cpp/classes-and-structs-cpp.md)   
 [结构和联合成员](../c-language/structure-and-union-members.md)