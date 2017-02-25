---
title: "编译器警告（等级 1）C4002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4002"
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”宏的实参太多  
  
 宏中的实参数量超过宏定义中的形参数量。 预处理器会收集额外参数，但会在宏扩展过程中忽略它们。  
  
 未正确使用 [Variadic 宏](../../preprocessor/variadic-macros.md) 时，可能会发生 C4002。  
  
 下面的示例生成 C4002：  
  
```  
// C4002.cpp // compile with: /W1 #define test(a) (a) int main() { int a = 1; int b = 2; a = test(a,b);   // C4002 // try.. a = test(a); }  
```  
  
 此错误还可能来自于为 Visual Studio .NET 2003 执行的编译器一致性工作：不再接受宏中的额外逗号。  
  
 编译器将不再接受宏中的额外逗号。 要使代码在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C\+\+ 中有效，请删除额外逗号。  
  
```  
// C4002b.cpp // compile with: /W1 #define F(x,y) int main() { F(2,,,,,,3,,,,,,)   // C4002 // Try the following line instead: // F(2,3) }  
```