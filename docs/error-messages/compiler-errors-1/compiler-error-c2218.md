---
title: "编译器错误 C2218 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2218"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2218"
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2218
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\_\_vectorcall”不能和“\/arch:IA32”一起使用  
  
 `__vectorcall` 调用约定仅受到包括流式处理 SIMD 扩展 2 \(SSE2\) 和更高版本的 x86 和 x64 处理器上的本机代码的支持。  有关详细信息，请参阅 [\_\_vectorcall](../../cpp/vectorcall.md)。  
  
 若要修复此错误，请将编译器选项更改为目标 SSE2、AVX 或 AVX2 指令集的。  有关详细信息，请参阅 [\/arch \(x86\)](../../build/reference/arch-x86.md)。