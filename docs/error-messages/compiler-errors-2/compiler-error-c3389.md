---
title: "编译器错误 C3389 | Microsoft Docs"
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
  - "C3389"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3389"
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3389
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_declspec\(keyword\) 不能与 \/clr:pure 或 \/clr:safe 一起使用  
  
 所用的 [\_\_declspec](../../cpp/declspec.md) 修饰符暗指按进程表示状态。[\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) 暗指按 [appdomain](../../cpp/appdomain.md) 表示状态。因此，不允许使用 `keyword` **\_\_declspec** 修饰符声明变量而使用 **\/clr:pure** 进行编译。  
  
 下面的示例生成 C3389：  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```