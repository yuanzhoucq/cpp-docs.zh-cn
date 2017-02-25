---
title: "编译器错误 C3909 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3909"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3909"
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3909
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

WinRT 或托管事件的声明必须出现在 WinRT 或托管类型中  
  
 Windows 运行时事件或托管事件是在本机类型中声明的。  要修复此错误，请在 Windows 运行时类型或托管类型中声明事件。  
  
 有关详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下面的示例生成 C3909，并演示如何修复此错误：  
  
```  
// C3909.cpp  
// compile with: /clr /c  
delegate void H();  
class X {  
   event H^ E;   // C3909 - use ref class X instead  
};  
  
ref class Y {  
   static event H^ E {  
      void add(H^) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```