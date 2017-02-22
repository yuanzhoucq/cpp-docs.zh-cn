---
title: "编译器错误 C3609 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3609"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3609"
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3609
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“成员”：密封的或最终函数必须是虚拟函数  
  
 [密封的](../../windows/sealed-cpp-component-extensions.md)和[最终](../../cpp/final-specifier.md)关键字仅允许在标记为 `virtual` 的类、结构或成员函数上使用。  
  
 以下示例生成 C3609：  
  
```  
// C3609.cpp  
// compile with: /clr /c  
ref class C {  
   int f() sealed;   // C3609  
   virtual int f2() sealed;   // OK  
};  
```  
  
 **C\+\+ 托管扩展**  
  
 以下示例生成 C3609：  
  
```  
// C3609c.cpp  
// compile with: /clr:oldSyntax /c  
__gc class C {  
   __sealed int f();   // C3609  
   __sealed virtual int f2();   // OK  
};  
```