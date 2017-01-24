---
title: "编译器警告（等级 4）C4913 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4913"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4913"
ms.assetid: b94aa52e-6029-4170-9134-017714931546
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4913
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**存在用户定义的二进制运算符“,”，但没有重载可以转换所有操作数，使用了默认的内置二进制运算符“,”**  
  
 对内置逗号运算符的调用发生在同样具有重载的逗号运算符的程序中；你认为可能已发生的转换没有发生。  
  
 下面的示例生成 C4913：  
  
```  
// C4913.cpp // compile with: /W4 struct A { }; struct S { }; struct B { // B() { } // B(S &s) { s; } }; B operator , (A a, B b) { a; return b; } int main() { A a; B b; S s; a, b;   // OK calls user defined operator a, s;   // C4913 uses builtin comma operator // uncomment the conversion code in B to resolve. }  
```