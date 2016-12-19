---
title: "编译器错误 C2537 | Microsoft Docs"
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
  - "C2537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2537"
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“specifier”: 非法的链接规范  
  
 可能的原因：  
  
1.  不支持这种链接说明符。  仅支持“C”链接说明符。  
  
2.  为一组重载函数中的多个函数指定了“C”链接。  这是不允许的。  
  
 下面的示例生成 C2537：  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```