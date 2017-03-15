---
title: "编译器错误 C2969 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2969"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2969"
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2969
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

语法错误: “symbol”: 成员函数定义应以“}”结尾  
  
 模板成员函数定义具有不匹配的右大括号。  
  
 以下示例生成 C2969：  
  
```  
// C2969.cpp // compile with: /c class A { int i; public: A(int i) {} }; A anA(1); class B { A a; B() : a(anA);   // C2969 // try the following line instead // B() : a(anA) {} };  
```