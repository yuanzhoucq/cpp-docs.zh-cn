---
title: "编译器警告（等级 1）C4561 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4561"
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器警告（等级 1）C4561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\_\_fastcall”与“\/clr”选项不兼容: 转换为“\_\_stdcall”  
  
 [\_\_fastcall](../../cpp/fastcall.md) 函数调用约定无法与 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译器选项一起使用。  编译器忽略对 `__fastcall` 的调用。  若要修复此警告，请移除对 **\_\_fastcall**  的调用或不使用 **\/clr** 进行编译。  
  
 下面的示例生成 C4561：  
  
```  
// C4561.cpp  
// compile with: /clr /W1 /c  
// processor: x86  
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve  
```