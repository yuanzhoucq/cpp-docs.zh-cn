---
title: "_crtDbgFlag | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_crtDbgFlag"
  - "crtDbgFlag"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_crtDbgFlag 常量"
  - "crtDbgFlag 常量"
  - "调试堆, 控制标志"
  - "调试堆, 跟踪内存"
  - "启用内存分配跟踪标志"
  - "内存分配, 跟踪标志"
  - "内存, 对调试堆进行跟踪"
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _crtDbgFlag
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\_crtDbgFlag** 标志由五个位域组成，这些字段可控制如何在堆的调试版本上跟踪、验证、报告和转储内存分配。  使用 [\_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 函数设置该标志的位域。  将在 Crtdbg.h 中声明此标志及其位域。  此标志仅当已在应用程序中定义 [\_DEBUG](../c-runtime-library/debug.md) 标志时才可用。  
  
 有关将此标志与其他调试函数结合使用的详细信息，请参阅[堆状态报告函数](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  
  
## 请参阅  
 [控制标志](../c-runtime-library/control-flags.md)