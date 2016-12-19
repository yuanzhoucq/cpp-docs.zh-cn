---
title: "编译器错误 C3655 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3655"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3655"
ms.assetid: 724919ab-2915-4b61-8794-44648e162d62
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3655
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数已显式重写  
  
 函数只能显式重写一次。  有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
 下面的示例生成 C3655：  
  
```  
// C3655.cpp  
// compile with: /clr /c  
public ref struct B {  
   virtual void f();  
   virtual void g();  
};  
  
public ref struct D : B {  
   virtual void f() new sealed = B::f;  
   virtual void g() new sealed = B::f;   // C3655  
   // try the following line instead  
   // virtual void g() new sealed = B::g;  
};  
```