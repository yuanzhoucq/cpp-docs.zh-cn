---
title: "编译器错误 C2931 | Microsoft Docs"
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
  - "C2931"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2931"
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2931
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: type\-class\-id 重新定义为“identifier”的成员函数  
  
 不能使用泛型或模板类作为另一个类的成员函数。  
  
 如果大括号匹配不正确，则可能导致此错误。  
  
 下面的示例生成 C2931：  
  
```  
// C2931.cpp // compile with: /c template<class T> struct TC { }; struct MyStruct { void TC<int>();   // C2931 }; struct TC2 { }; struct MyStruct2 { void TC2(); };  
```  
  
 使用泛型时也可能发生 C2931：  
  
```  
// C2931b.cpp // compile with: /clr /c generic<class T> ref struct GC {}; struct MyStruct { void GC<int>();   // C2931 void GC2();   // OK };  
```