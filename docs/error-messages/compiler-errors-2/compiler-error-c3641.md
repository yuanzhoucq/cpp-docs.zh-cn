---
title: "编译器错误 C3641 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3641"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3641"
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3641
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 用 \/clr:pure 或 \/clr:safe 编译的函数的调用约定“calling\_convention”无效  
  
 只允许将 [\_\_clrcall](../../cpp/clrcall.md) 调用约定与 [\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) 一起使用。  
  
 下面的示例生成 C3641：  
  
```  
// C3641.cpp  
// compile with: /clr:pure /c  
void __cdecl f() {}   // C3641  
```