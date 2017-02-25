---
title: "资源编译器错误 RW2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2001"
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RW2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

预处理 RC 文件中的指令无效  
  
 RC 文件包含 **\#pragma** 指令。  
  
 对资源编译器在处理包含文件时定义的 **RC\_INVOKED** 常数使用 **\#ifndef** 预处理器指令。  将 **\#pragma** 指令放在定义 **RC\_INVOKED** 常数时不处理的代码块中。  此块中的代码只被 C\/C\+\+ 编译器处理，不被资源编译器处理。  以下代码示例演示此技术：  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 **\#pragma** 预处理器指令在 .RC 文件中没有意义。  **\#include** 预处理器指令在 .RC 文件中被频繁使用以包括头文件（要么是基于项目的自定义头文件，要么是 Microsoft 通过其产品之一提供的标准头文件）。  这些包含文件中有一些包含 **\#pragma** 指令。  由于一个头文件可以包括一个或多个其他头文件，包含有问题的 **\#pragma** 指令的文件不可能立刻显而易见。  
  
 **\#ifndef RC\_INVOKED** 技术可以控制将头文件包含在基于项目的头文件中。