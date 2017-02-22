---
title: "编译器错误 C2732 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2732"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2732"
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2732
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

链接规范与“function”的早期规范冲突  
  
 该函数已经使用其他链接说明符声明。  
  
 具有不同链接说明符的包含文件可能会导致此错误。  
  
 要修复此错误，请更改 `extern` 语句，以便这些链接一致。  特别是，不要对 `extern "C"` 块中的 `#include` 指令换行。  
  
## 示例  
 下面的示例生成 C2732：  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```