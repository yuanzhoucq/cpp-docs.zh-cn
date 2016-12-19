---
title: "编译器错误 C3299 | Microsoft Docs"
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
  - "C3299"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3299"
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3299
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member\_function”：无法指定约束，因为它们都继承自基方法  
  
 替代泛型成员函数时，无法指定约束子句（重复约束意味着未继承约束）。  
  
 将继承正在替代的泛型函数上的约束子句。  
  
 有关详细信息，请参阅[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3299。  
  
```  
// C3299.cpp // compile with: /clr /c public ref struct R { generic<class T> where T : R virtual void f(); }; public ref struct S : R { generic<class T> where T : R   // C3299 virtual void f() override; };  
```