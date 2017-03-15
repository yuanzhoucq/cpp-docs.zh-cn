---
title: "if-else 语句 (C++) | Microsoft Docs"
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
  - "else_cpp"
  - "else"
  - "if_cpp"
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "else 关键字 [C++]"
  - "if 关键字 [C++]"
  - "if 关键字 [C++], if-else"
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# if-else 语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制条件分支。  
  
## 语法  
  
```  
  
      if ( expression )  
   statement1  
[else  
   statement2]  
```  
  
## 备注  
 如果 *expression* 的值不为零，执行 *statement1* 。  如果选项 **else** 存在，如果 *expression* 的值为零，执行 *statement2*。  *表达式*必须是算术或指针类型，或者必须是定义明确的整型或指针类型转换的类类型。有关转换器的信息，请参见[标准转换](../cpp/standard-conversions.md)。  
  
 在两个形式的 **if** 语句和 *expression* 语句中计算，可以具有除结构以外的任何值，包括所有副作用。  除非 *statement* 中的一个包含 [break](../cpp/break-statement-cpp.md)、 [continue](../cpp/continue-statement-cpp.md) 或 [goto](../cpp/goto-statement-cpp.md)，控件才能从 **if** 语句传递到项目中的下一条语句。  
  
 `if...else` 语句的 **else** 子句与在没有相应的 **else** 语句的同一范围的最接近的前面 **if** 语句相关。  
  
 为了使此示例可以明确有关 `if...else` 配对，取消对大括号的注释。  
  
## 示例  
  
```  
// if_else_statement.cpp  
#include <stdio.h>  
  
int main()   
{  
   int x = 0;  
   if (x == 0)  
   {  
      printf_s("x is 0!\n");  
   }  
   else  
   {  
      printf_s("x is not 0!\n"); // this statement will not be executed  
   }  
  
   x = 1;  
   if (x == 0)  
   {  
      printf_s("x is 0!\n"); // this statement will not be executed  
   }  
   else  
   {  
      printf_s("x is not 0!\n");  
   }  
  
   return 0;  
}  
```  
  
  **x 是 0！**  
**x 不是 0\!**   
## 请参阅  
 [选择语句](../cpp/selection-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [switch 语句 \(C\+\+\)](../cpp/switch-statement-cpp.md)