---
title: "检查内存改写 | Microsoft Docs"
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
helpviewer_keywords: 
  - "内存, 改写"
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 检查内存改写
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果在调用堆操作函数时发生访问冲突，有可能是程序损坏了堆。  这种情况的通常症状是：  
  
```  
Access Violation in _searchseg  
```  
  
 [\_heapchk](../../c-runtime-library/reference/heapchk.md) 函数在调试版本和发布版本（仅适用于 Windows NT）中都可用于验证运行库堆的完整性。  可以用与 `AfxCheckMemory` 函数基本相同的方法使用 `_heapchk` 来找出堆覆盖，例如：  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 如果此函数失败，则需要找出堆发生损坏的位置。  
  
## 请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)