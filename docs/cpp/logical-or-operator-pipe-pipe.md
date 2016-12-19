---
title: "逻辑或运算符：|| | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "|| 运算符"
  - "逻辑 OR 运算符"
  - "OR 运算符"
  - "OR 运算符, 逻辑"
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逻辑或运算符：||
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## 备注  
 如果任一操作数或两个操作数为 **true**，则逻辑“或”运算符 \(`||`\) 返回布尔值 **true**；否则返回 **false**。  操作数在计算之前隐式转换为类型 `bool`，结果的类型为 `bool`。  逻辑“或”具有从左向右的关联性。  
  
 逻辑“或”运算符的操作数不需要是同一类型，但是它们必须是整型或指针类型。  操作数通常为关系或相等表达式。  
  
 第一个操作数将完全计算，并且在继续计算逻辑“或”表达式之前将完成所有副作用。  
  
 仅当第一个操作数的计算结果为 false \(0\) 时计算第二个操作数。  在逻辑“或”表达式为 true 时，这将消除对第二个操作数的不必要的计算。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在上面的示例中，如果 `x` 与 `w`、`y` 或 `z` 相等，则 `printf` 函数的第二个参数的计算结果将为 true，并打印值 1。  否则，它的计算结果将为 false，并打印值 0。  只要其中一个条件的计算结果为 true，计算便会停止。  
  
## &#124;&#124; 的运算符关键字  
 **or** 运算符是 `||` 的等效文本。  在您的程序中有两种访问 **or** 运算符的方法：包括头文件 `iso646.h` 或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Logical_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical OR  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b || b > c yields "  
         << (a < b || b > c) << endl  
         << "The false expression "  
         << "a > b || b > c yields "  
         << (a > b || b > c) << endl;  
}  
```  
  
## 请参阅  
 [逻辑运算符](../misc/logical-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 逻辑运算符](../c-language/c-logical-operators.md)