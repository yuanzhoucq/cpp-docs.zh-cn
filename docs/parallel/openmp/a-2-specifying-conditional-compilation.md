---
title: "A.2   Specifying Conditional Compilation | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.2   Specifying Conditional Compilation
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例演示如何使用条件编译使用 OpenMP 宏 `_OPENMP` \(在第 8 页\) 的[第2.2部分](../../parallel/openmp/2-2-conditional-compilation.md) 。  OpenMP 生成， `_OPENMP` 宏变为定义。  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 定义的预处理器运算符在单个指令允许多个宏测试。  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```