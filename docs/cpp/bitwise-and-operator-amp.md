---
title: "按位与运算符：&amp; | Microsoft Docs"
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
  - "bitand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 运算符, 按位运算符"
  - "AND 运算符"
  - "按位运算符, AND 运算符"
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 按位与运算符：&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
expression   
&  
 expression  
  
```  
  
## 备注  
 表达式可以是其他“与”表达式，或（遵循下面所述的类型限制）相等表达式、关系表达式、加法表达式、乘法表达式、指向成员的指针表达式、强制转换表达式、一元表达式、后缀表达式或主表达式。  
  
 按位“与”运算符 \(**&**\) 会将第一操作数的每一位与第二操作数的相应位进行比较。  如果两个位均为 1，则对应的结果位将设置为 1。  否则，将对应的结果位设置为 0。  
  
 按位“与”运算符的两个操作数必须为整型。  [算术转换](../misc/arithmetic-conversions.md)中所述的常用算术转换将应用于操作数。  
  
## & 的运算符关键字  
 `bitand` 运算符是 **&** 的文本等效项。  访问程序中的 `bitand` 运算符的方式有两种：包括头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Bitwise_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise AND  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0xFFFF;      // pattern 1111 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...  
}  
```  
  
## 请参阅  
 [C\+\+ 按位运算符](../misc/cpp-bitwise-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 按位运算符](../c-language/c-bitwise-operators.md)