---
title: "二进制求补运算符：~ | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~ 运算符, 语法"
  - "按位求补运算符"
  - "求补运算符"
  - "二进制求补运算符"
  - "波形符 (~) 二进制求补运算符"
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 二进制求补运算符：~
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
~ cast-expression  
```  
  
## 备注  
 二进制反码运算符 \(`~`\)（有时称为“按位反码”运算符）将生成其操作数的按位二进制反码。  即，操作数中为 1 的每个位在结果中为 0。  相反，操作数中为 0 的每个位在结果中为 1。  二进制反码运算符的操作数必须为整型。  
  
## ~ 的运算符关键字  
 `compl` 运算符是 `~` 的文本等效项。  访问程序中的 `compl` 运算符有两种方式：包括头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md) 进行编译。  
  
## 示例  
  
```  
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 在此示例中，分配给 `y` 的新值是无符号值 0xFFFF 或 0x0000 的二进制反码。  
  
 将对整型操作数执行整型提升，并且结果类型将是操作数将提升到的类型。  有关如何完成提升的详细信息，请参阅[整型提升](../misc/integral-promotions.md)。  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算术运算符](../c-language/unary-arithmetic-operators.md)