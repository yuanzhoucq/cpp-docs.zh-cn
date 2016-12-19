---
title: "编译器错误 C3734 | Microsoft Docs"
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
  - "C3734"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3734"
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3734
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 托管或 WinRT 类不能是组件类  
  
 [coclass](../../windows/coclass.md) 特性不能与托管或 WinRT 类一起使用。  
  
 下面的示例生成 C3734，并演示如何修复此错误：  
  
```  
// C3734.cpp  
// compile with: /clr /c  
[module(name="x")];  
  
[coclass]  
ref class CMyClass {   // C3734 remove the ref keyword to resolve  
};  
```  
  
 下面的示例生成 C3734，并演示如何修复此错误：  
  
```  
// C3734_b.cpp  
// compile with: /clr:oldSyntax /c  
[module(name="x")];  
  
[coclass]  
__gc class CMyClass {   // C3734 remove the __gc keyword to resolve  
};  
```