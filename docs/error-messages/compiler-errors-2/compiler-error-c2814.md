---
title: "编译器错误 C2814 | Microsoft Docs"
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
  - "C2814"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2814"
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2814
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”：本机类型不能嵌套在托管类型或 WinRT 类型“type”内  
  
## 示例  
 本机类型不能嵌套在 CLR 或 WinRT 类型中。  下面的示例生成 C2814，并演示如何修复此错误。  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
  
## 示例  
 使用 C\+\+ 托管扩展，则必须使用以下关键字之一显式指定嵌入类型的“托管状态”：[\_\_gc](../../misc/gc.md)、[\_\_nogc](../../misc/nogc.md) 或 [\_\_value](../../misc/value.md)。  
  
 下面的示例生成 C2814，并演示如何修复此错误。  
  
```  
// C2814_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc class A {  
   class B {};   // C2814  
   __gc class C {};   // OK  
};  
```