---
title: "编译器错误 C3253 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3253"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3253"
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3253
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 显式重写时出错  
  
 未正确指定显式重写。  例如，不能为一个已指定为纯函数的重写指定实现。  有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下面的示例生成 C3253：  
  
```  
// C3253.cpp  
// compile with: /clr  
public interface struct I {  
   void a();  
   void b();  
   void c();  
};  
  
public ref struct R : I {  
   virtual void a() = 0, I::a {}   // C3253  
   virtual void b() = I::a {}   // OK  
   virtual void c() = 0;   // OK  
};  
```