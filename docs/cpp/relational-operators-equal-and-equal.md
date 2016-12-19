---
title: "关系运算符：&lt;、&gt;、&lt;= 和 &gt;= | Microsoft Docs"
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
  - "<"
  - ">"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< 运算符"
  - "<= 运算符"
  - "> 运算符"
  - ">= 运算符"
  - "大于运算符"
  - "大于或等于运算符"
  - "小于运算符"
  - "小于或等于运算符"
  - "关系运算符, 语法"
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 关系运算符：&lt;、&gt;、&lt;= 和 &gt;=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
        expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## 备注  
 二进制关系运算符确定下列关系：  
  
-   小于 \(**\<**\)  
  
-   大于 \(**\>**\)  
  
-   小于或等于 \(**\<\=**\)  
  
-   大于或等于 \(**\>\=**\)  
  
 关系运算符具有从左到右的关联性。  关系运算符的两个操作数必须是算术或指针类型。  它们将生成 `bool` 类型的值。  如果表达式中的关系为 false，则返回的值为 **false** \(0\)；否则返回的值为 **true** \(1\)。  
  
## 示例  
  
```  
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 前面的示例中的表达式必须括在括号中，因为流插入运算符 \(**\<\<**\) 的优先级高于关系运算符。  因此，未括在括号中的第一个表达式的计算结果将为：  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 [算术转换](../misc/arithmetic-conversions.md)中介绍的常用算术转换将应用于算术类型的操作数。  
  
## 比较指针  
 在比较两个指向同一类型的对象的指针时，结果由程序的地址空间中所指向的对象的位置决定。  也可以将指针与计算结果为 0 的常量表达式或 void \* 类型的指针进行比较。  如果针对 void \* 类型的指针执行指针比较，则另一个指针将隐式转换为 void \* 类型。  然后进行比较。  
  
 不能比较两个类型不同的指针，除非：  
  
-   一个类型是派生自另一个类型的类类型。  
  
-   至少有一个指针显式转换（强制转换）为类型 void \*。  （对于该转换，另一个指针将隐式转换为类型 void \*。）  
  
 两个指向同一对象的相同类型的指针一定是相等的。  如果比较两个指向对象的非静态成员的指针，则以下规则将适用：  
  
-   如果类类型不是联合，并且如果两个成员未通过 *access\-specifier*（例如，公共、受保护的或私有）分隔开，则指向最后声明的成员的指针将大于指向之前声明的成员的指针。  （有关 *access\-specifier* 的信息，请参阅[访问说明符](../misc/access-specifiers.md)中的“语法”一节。）  
  
-   如果两个成员通过 *access\-specifier* 分隔开，则结果是不确定的。  
  
-   如果类类型是联合，则指向该联合中不同的数据成员的指针是相等的。  
  
 如果两个指针指向同一数组的元素或指向超出数组末尾 1 的元素，则指向带较高下标的对象的指针会更高。  仅当指针引用同一数组中的对象或超出数组末尾 1 的位置时，才能保证指针比较有效。  
  
## 请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 关系和相等运算符](../c-language/c-relational-and-equality-operators.md)