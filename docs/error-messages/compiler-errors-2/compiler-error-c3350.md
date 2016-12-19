---
title: "编译器错误 C3350 | Microsoft Docs"
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
  - "C3350"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3350"
ms.assetid: cfbbc338-92b5-4f34-999e-aa2d2376bc70
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3350
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“delegate”: 委托构造函数需要 number 个参数  
  
 创建委托实例时，必须传递两个参数，一个是包含委托函数的类型的实例，一个是该函数。  
  
 下面的示例生成 C3350：  
  
```  
// C3350.cpp // compile with: /clr delegate void SumDelegate(); public ref class X { public: void F() {} static void F2() {} }; int main() { X ^ MyX = gcnew X(); SumDelegate ^ pSD = gcnew SumDelegate();   // C3350 SumDelegate ^ pSD1 = gcnew SumDelegate(MyX, &X::F); SumDelegate ^ pSD2 = gcnew SumDelegate(&X::F2); }  
```  
  
 **C\+\+ 托管扩展**  
  
 下面的示例生成 C3350：  
  
```  
// C3350b.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> __delegate void SumDelegate(); public __gc class X { public: void F() {} static void F2() {} }; int main() { X * MyX = new X(); SumDelegate *pSD = new SumDelegate();   // C3350 SumDelegate *pSD1 = new SumDelegate(MyX, &X::F); SumDelegate *pSD2 = new SumDelegate(&X::F2); }  
```