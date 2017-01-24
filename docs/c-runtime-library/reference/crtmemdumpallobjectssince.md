---
title: "_CrtMemDumpAllObjectsSince | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtMemDumpAllObjectsSince"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "CrtMemDumpAllObjectsSince"
  - "_CrtMemDumpAllObjectsSince"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CrtMemDumpAllObjectsSince 函数"
  - "CrtMemDumpAllObjectsSince 函数"
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtMemDumpAllObjectsSince
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从程序执行的开始或从指定的堆状态（仅限调试版本）转储关于在堆中对象的信息。  
  
## 语法  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### 参数  
 `state`  
 指向堆状态开始转储或为 **NULL** 的指针。  
  
## 备注  
 `_CrtMemDumpAllObjectsSince` 函数转储分配在堆中对象的调试头信息到用户可读的表格中。  转储信息可以被应用程序跟踪配置和检测内存问题使用。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtMemDumpAllObjectsSince` 的调用。  
  
 `_CrtMemDumpAllObjectsSince` 使用`state` 参数的值来确定哪里开始转储操作。  从指定的堆状态开始转储，`state` 参数必须是在调用`_CrtMemDumpAllObjectsSince` 之前，指向由 [\_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 填充的 **\_CrtMemState** 结构的指针。  当 `state` 为 **NULL** 时，该函数从项目执行起开始转储。  
  
 如果应用程序通过调用 [\_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md) 安装一个转储挂钩函数，那么每次 `_CrtMemDumpAllObjectsSince` 转储关于块的 `_CLIENT_BLOCK` 类型的信息，则也调用应用程序提供的转储函数。  默认情况下，内部 C 运行时块 \(`_CRT_BLOCK`\) 不包括内存转储操作。  [\_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函数可以用来打开**\_crtDbgFlag** 的 `_CRTDBG_CHECK_CRT_DF` 位用来包含这些块。  此外，被标记为释放或忽略的块（**\_FREE\_BLOCK**、**\_IGNORE\_BLOCK**）不包括在内存转储中。  
  
 有关堆状态函数的详细信息和 `_CrtMemState`结构，请参见 [堆状态报告函数](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  有关在调试版本中的基位置堆中内存如何分配，初始化和管理的详细信息，请参见 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**\_CrtMemDumpAll\-ObjectsSince**|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
 对于如何使用 `_CrtMemDumpAllObjectsSince` 的例子，请参阅 [crt\_dbg2](http://msdn.microsoft.com/zh-cn/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)