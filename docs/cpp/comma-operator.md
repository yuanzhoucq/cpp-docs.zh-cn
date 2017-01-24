---
title: "逗号运算符：, | Microsoft Docs"
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
  - "%2C"
  - ","
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "逗号运算符"
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逗号运算符：,
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

允许对两个语句进行分组，其中有一个是预期的。  
  
## 语法  
  
```  
  
expression , expression  
```  
  
## 备注  
 逗号运算符具有从左向右的关联性。  由逗号分隔的两个表达式将从左向右进行计算。  始终计算左操作数，并且在计算右操作数之前将完成所有副作用。  
  
 在某些上下文（如函数参数列表）中，逗号可用作分隔符。  不要将该逗号用作分隔符与将其用作运算符的情况混淆；这两种用法完全不同。  
  
 考虑表达式  
  
 *e1* , *e2*  
  
 该表达式的类型和值是 *e2* 的类型和值；*e1* 的计算结果将被丢弃。  如果右操作数是左值，则结果为左值。  
  
 在通常将逗号用作分隔符的方案中（例如，在函数或聚合初始值设定项的实参中），逗号运算符及其操作数必须包含在括号中。  例如：  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 在上面的对 `func_one` 的函数调用中，会传递以逗号分隔的三个参数：`x`、`y + 2` 和 `z`。  在对 `func_two` 的函数调用中，圆括号强制编译器将第一个逗号解释为顺序计算运算符。  此函数调用将两个参数传递给 `func_two`。  第一个参数是顺序计算运算 `(x--, y + 2)` 的结果，具有表达式 `y + 2` 的值和类型；第二个参数为 `z`。  
  
## 示例  
  
```  
// cpp_comma_operator.cpp  
#include <stdio.h>  
int main () {  
   int i = 10, b = 20, c= 30;  
   i = b, c;  
   printf("%i\n", i);  
  
   i = (b, c);  
   printf("%i\n", i);  
}  
```  
  
  **20**  
**30**   
## 请参阅  
 [使用二元运算符的表达式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 运算符](../misc/cpp-operators.md)   
 [C\+\+ 运算符优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [顺序评估运算符](../c-language/sequential-evaluation-operator.md)