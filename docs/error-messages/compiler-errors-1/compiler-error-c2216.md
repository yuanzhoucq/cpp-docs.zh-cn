---
title: "编译器错误 C2216 | Microsoft Docs"
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
  - "C2216"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2216"
ms.assetid: 250f6bdc-a5e1-495f-a1e8-6e8e7021ad9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2216
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“keyword1”不能和“keyword2”一起使用  
  
 一起使用两个互相排斥的关键字。  
  
## 示例  
 下面的示例生成 C2216。  
  
```  
// C2216.cpp // compile with: /clr /c ref struct Y1 { literal static int staticConst2 = 10;   // C2216 };  
```  
  
## 示例  
 下面的示例生成 C2216。  
  
```  
// C2216b.cpp // compile with: /clr /c public ref class X { extern property int i { int get(); }   // C2216 extern not allowed on property typedef property int i2;   // C2216 typedef not allowed on property };  
```  
  
## 示例  
 下面的示例生成 C2216。  
  
```  
// C2216c.cpp // compile with: /clr /c public interface struct I { double f(); double g(); double h(); }; public ref struct R : I { virtual double f() new override { return 0.0; }   // C2216 virtual double g() new { return 0.0; }   // OK virtual double h() override { return 0.0; }   // OK };  
```