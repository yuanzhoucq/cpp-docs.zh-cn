---
title: "4. Environment Variables | Microsoft Docs"
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
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4. Environment Variables
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

描述本章 OpenMP C 和 C\+\+ API 环境变量 \(或等效的特定于平台的结构\) 该控件并行代码的执行。  环境变量的名称必须大写。  值赋给它们不区分大小写，可具有、前导和尾随空格。  为值的修改在程序在启动后已被忽略。  
  
 环境变量如下所示:  
  
-   **OMP\_SCHEDULE** 设置运行时安排类型和块范围。  
  
-   **OMP\_NUM\_THREADS** 设置线程数在执行时使用。  
  
-   **OMP\_DYNAMIC** 启用或禁用线程数动态调整。  
  
-   **OMP\_NESTED** 启用或禁用嵌套并行。  
  
 在本章的示例仅演示这些变量如何在 UNIX C shell \(csh\) 环境中可能设置。  在 Korn shell 和 DOS 环境事件是相似的，如下所示:  
  
 csh:  
 “dynamic”的 setenv OMP\_SCHEDULE  
  
 ksh:  
 " dynamic”的导出 OMP\_SCHEDULE\=  
  
 DOS:  
 设置 " dynamic”的 OMP\_SCHEDULE\=