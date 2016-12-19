---
title: "逻辑非运算符：! | Microsoft Docs"
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
  - "!"
  - "Not"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! 运算符"
  - "逻辑非"
  - "NOT 运算符"
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逻辑非运算符：!
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
! cast-expression  
```  
  
## 备注  
 逻辑求反运算符 \(**\!**\) 反转其操作数的含义。  操作数必须是算法或指针类型（或计算结果为算法或指针类型的表达式）。  操作数将隐式转换为类型 `bool`。  如果已转换的操作数是 **false**，则结果是 **true**；如果已转换的操作数是 **true**，则结果是 **false**。  结果为 `bool` 类型。  
  
 对于表达式 *e*，一元运算符表达式 **\!***e* 与该表达式 **\(***e* `==` 0\) 等效，涉及重载运算符的情况除外。  
  
## \! 的运算符关键字  
 **not** 运算符是与 **\!** 等效文本。  在您的程序中，可通过两种方法访问 **not** 运算符：包含头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## 请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [一元算术运算符](../c-language/unary-arithmetic-operators.md)