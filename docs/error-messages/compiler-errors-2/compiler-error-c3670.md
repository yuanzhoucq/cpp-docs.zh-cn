---
title: "编译器错误 C3670 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3670"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3670"
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3670
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“override”: 不能重写不可访问的基类方法“method”  
  
 只有其访问级别使其可用于派生类型的函数才能进行重写。  有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下面的示例生成 C3670：  
  
```  
// C3670.cpp  
// compile with: /clr /c  
public ref class C {  
// Uncomment the following line to resolve.  
// public:  
   virtual void g() { }  
};  
  
public ref class D : public C {  
public:  
   virtual void f() new sealed = C::g {};   // C3670  
};  
```