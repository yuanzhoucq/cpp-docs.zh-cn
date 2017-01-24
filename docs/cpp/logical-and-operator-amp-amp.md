---
title: "逻辑与运算符：&amp;&amp; | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "&& 运算符"
  - "AND 运算符"
  - "逻辑 AND 运算符"
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逻辑与运算符：&amp;&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## 备注  
 如果操作数为 **true**，则逻辑“与”运算符 \(**&&**\) 返回布尔值 **true**，否则返回 **false**。  操作数在计算之前隐式转换为类型 `bool`，结果的类型为 `bool`。  逻辑“与”具有从左到右的关联性。  
  
 逻辑“与”运算符的操作数不需要具有相同的类型，但它们必须是整数或指针类型。  操作数通常为关系或相等表达式。  
  
 第一个操作数将完全计算，在继续对逻辑“与”表达式进行计算前将完成所有副作用。  
  
 如果第一个操作数的计算结果为 true（非零），则计算第二个操作数。  当逻辑“与”表达式为 false 时，这种计算方式可消除不必要的对第二个操作数的计算。  可以使用此短路计算防止 null 指针取消引用，如以下示例所示：  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 如果 `pch` 为 null \(0\)，则从不计算表达式的右侧。  因此，无法通过 null 指针进行赋值。  
  
## && 的运算符关键字  
 **and** 运算符是 **&&** 的文本等效项。  您的程序中有两种访问 **and** 运算符的方法：包含标头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## 请参阅  
 [逻辑运算符](../misc/logical-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 逻辑运算符](../c-language/c-logical-operators.md)