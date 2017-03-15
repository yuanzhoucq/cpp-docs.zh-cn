---
title: "Lvalues 和 Rvalues | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "L-values"
  - "R-values"
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Lvalues 和 Rvalues
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个 C\+\+ 表达式是左值或右值。  左值是指在单个表达式的外部保留的对象。  可以将左值视为具有名称的对象。  所有变量（包括不能更改的 \(`const`\) 变量）都是左值。  左值是一个不在使用它的表达式的外部保留的临时值。  若要更好地了解左值和右值之间的区别，请考虑下面的示例：  
  
```  
// lvalues_and_rvalues1.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
   int x = 3 + 4;  
   cout << x << endl;  
}  
```  
  
 在此示例中，`x` 是左值，因为它在定义它的表达式的外部保留。  表达式 `3 + 4` 是为一个右值，因为其计算结果为不在定义它的表达式的外部保留的临时值。  
  
 以下示例演示左值和右值的多种正确的和错误的用法：  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  此主题中的示例阐释了未重载运算符时的正确和错误用法。  通过重载运算符，可以使表达式（如 `j * 4`）成为左值。  
  
 当引用对象引用时，通常会使用术语“左值”和“右值”。  有关引用的详细信息，请参阅[Lvalue 引用声明符：&](../cpp/lvalue-reference-declarator-amp.md) 和[规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 请参阅  
 [基本概念](../cpp/basic-concepts-cpp.md)   
 [Lvalue 引用声明符：&](../cpp/lvalue-reference-declarator-amp.md)   
 [规则引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)