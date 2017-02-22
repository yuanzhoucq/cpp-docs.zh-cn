---
title: "控制标志 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调试堆, 控制标志"
  - "标志, 控件"
  - "堆分配, 控制标志"
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 控制标志
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft C 运行库的调试版本使用以下标志控制堆分配以及报告进程。  有关更多信息，请参见[CRT 调试技术](../Topic/CRT%20Debugging%20Techniques.md)。  
  
|Flag|说明|  
|----------|--------|  
|[\_CRTDBG\_MAP\_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|映射基堆函数将调试复制版本|  
|[\_DEBUG](../c-runtime-library/debug.md)|启用使用运行时函数的" Debug "版本|  
|[\_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|控件调试堆管理器如何跟踪分配|  
  
 这些标志可以定义用 \/D 命令行选项或 `#define` 指令。  当标志定义使用 `#define`，指令必须在例程声明的头文件包括语句之前出现。  
  
## 请参阅  
 [全局变量和标准类型](../c-runtime-library/global-variables-and-standard-types.md)