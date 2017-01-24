---
title: "相等运算符：== 和 != | Microsoft Docs"
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
  - "not_eq"
  - "!="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 运算符"
  - "== 运算符"
  - "等于运算符"
  - "相等运算符"
  - "相等运算符, 语法"
  - "不等于比较运算符"
  - "not_eq 运算符"
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 相等运算符：== 和 !=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
      expression == expression  
expression != expression  
```  
  
## 备注  
 二元相等运算符将严格比较其操作数的相等性或不相等性。  
  
 相等运算符（等于 \(`==`\) 而不等于 \(`!=`\)）的优先级低于关系运算符的优先级，但其行为类似。  这些运算符的结果类型为 `bool`。  
  
 如果这两个操作数具有相同的值，则相等运算符 \(`==`\) 返回 **true** \(1\)；否则返回 **false** \(0\)。  如果操作数不具有相同的值，则不相等运算符 \(`!=`\) 返回 **true**；否则返回 **false**。  
  
## \!\= 的运算符关键字  
 `not_eq` 运算符是 `!=` 的文本等效项。  访问程序中的 `not_eq` 运算符的方式有两种：包括头文件 `iso646.h`，或使用 [\/Za](../build/reference/za-ze-disable-language-extensions.md)（禁用语言扩展）编译器选项进行编译。  
  
## 示例  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 相等运算符可比较指向同一类型的成员的指针。  在此类比较中，将执行在[指向成员的指针转换](../misc/pointer-to-member-conversions.md)中讨论的指向成员的指针转换。  指向成员的指针也可以与计算结果为 0 的常量表达式进行比较。  
  
## 请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 关系和相等运算符](../c-language/c-relational-and-equality-operators.md)