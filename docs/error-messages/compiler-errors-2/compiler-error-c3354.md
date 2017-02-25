---
title: "编译器错误 C3354 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3354"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3354"
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3354
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“%$I”：该函数用于创建不能有返回类型“type”的委托  
  
 以下类型作为[委托](../../misc/delegate.md)的返回类型无效：  
  
-   指向函数的指针  
  
-   指向成员的指针  
  
-   指向成员函数的指针  
  
-   对函数的引用  
  
-   对成员函数的引用  
  
 以下示例生成 C3354：  
  
```  
// C3354_2.cpp // compile with: /clr /c using namespace System; typedef void ( *VoidPfn )(); delegate VoidPfn func(); // C3354 // try the following line instead // delegate  void func();  
```  
  
 以下示例生成 C3354：  
  
```  
// C3354.cpp // compile with: /clr:oldSyntax /c #using <mscorlib.dll> using namespace System; typedef void (*VoidPfn)(); __delegate VoidPfn func();   // C3354 // try the following line instead // __delegate void func();  
```